# Document templates

## Document Templates&#x20;

This guide documents how to author the HTML body of an **Document Template.** The body is a [LiquidJS](https://liquidjs.com/) template that is rendered **client-side & server-side**, against the document's data.

It applies to documents shown in the **record File viewer.**

***

### 1. How rendering works

* Your template is plain HTML with Liquid tags (`{{ ... }}`, `{% ... %}`).
* It is rendered against a **context** (the variables below) using LiquidJS with a set of custom filters (section 4).
* Rendering happens in the browser from the document's stored data, so it works **offline** and **re-renders live** when the user changes the selection.
* All standard LiquidJS tags and filters are available (`if`, `for`, `assign`, `unless`, `case`, `capture`, `json`, `default`, `date`, `upcase`, …) **in addition** to the custom filters documented here.
* If the template fails to compile/render, the viewer shows an error card instead of the document.

> **Page format / orientation** (A4, portrait, …) are template _settings_, not Liquid variables. They control the rendered page size and the PDF export.

***

### 2. Key conventions

#### 2.1 Variable keys use underscores (not dots)

Record fields are keyed by their cube path with **dots replaced by underscores**. A field whose cube path is `Tab_8880.prop878` is read as:

```liquid
{{ record.Tab_8880_prop878 }}
```

#### 2.2 Label values are encoded as `id||name||image`

Many fields (foreign keys, labels) hold a packed string `id||name||image`. Use the `extractLabelValue` filter to pull out a part:

```liquid
{{ record.Tab_8879_label | extractLabelValue: "name" }}
```

***

### 3. Available variables

| Variable            | Type   | What it holds                                    |
| ------------------- | ------ | ------------------------------------------------ |
| `record`            | object | The document's record (fields, underscore-keyed) |
| `user`              | object | The current user                                 |
| `org`               | object | The current organisation                         |
| `selections`        | array  | The **selected** records (+ quantity)            |
| `all_records`       | array  | **Every** record (+ optional quantity)           |
| `available_actions` | array  | Every record, display-formatted                  |

#### `record`

The record the document is attached to. Keys are the record's fields in underscore form (see 2.1). Values are raw cube values; label-type values use the `id||name||image` encoding.

For a **fanOut** document the record is the **merge of the parent and the drilled-into record** (e.g. both `Store.*` and `StorePromo.*` fields), so both sets of fields are addressable:

```liquid
<h1>{{ record.Store_name | extractLabelValue: "name" }}</h1>
<h2>{{ record.StorePromo_label | extractLabelValue: "name" }}</h2>
```

#### `user`

The signed-in user. Reliable fields:

| Field            | Example           |
| ---------------- | ----------------- |
| `user.firstName` | `"Jane"`          |
| `user.lastName`  | `"Doe"`           |
| `user.email`     | `"jane@acme.com"` |

```liquid
Prepared by {{ user.firstName }} {{ user.lastName }} — {{ user.email }}
```

#### `org`

The current organisation. Reliable fields: `org.id`, `org.name`.

```liquid
{{ org.name }}
```

#### `selections`

The records the user has **selected** in the selection panel. Re-computed live as the selection changes. Each entry:

```jsonc
{
  "record":   { /* fields, underscore-keyed */ },
  "quantity": 12,            // or null — the "number" selection value
  "metadata": { "category": "...", "bucket": "...", "lever": "..." }
}
```

Iterate it with `getSelectedRecords` (recommended — see below) so each item is flattened to its record fields **plus** `quantity`:

```liquid
{% assign items = selections | getSelectedRecords %}
{% for item in items %}
  {{ item.Tab_8880_prop878 | extractLabelValue: "name" }} × {{ item.quantity }}
{% endfor %}
```

> For records produced from an Object Link, `metadata.category`, `metadata.bucket` and `metadata.lever` are **all the Object Link's name**.

#### `all_records`

Same shape as `selections`, but contains **every** record (selected or not). `quantity` is the entered number when present, otherwise `null`. Use it when you want to list everything regardless of selection. Pair it with `getRecordsWithQuantity` or `getSelectedRecords`:

```liquid
{% assign all = all_records | getRecordsWithQuantity %}
{% for item in all %}
  {{ item.Tab_8880_prop878 | extractLabelValue: "name" }} — {{ item.quantity | default: 0 }}
{% endfor %}
```

#### `available_actions`

Every record, pre-formatted for display. Each entry:

```jsonc
{
  "id": "<objectLinkId>-<recordId>",
  "category": "...",
  "lever": "...",
  "selectionType": "boolean" | "number" | "ObjectLink",
  "objectId": "...",
  "objectLinkId": "...",
  "original":  { /* fields, underscore-keyed */ },
  "formatted": {
    "id": "...",
    "label": "Promo Summer 2026",   // resolved display label
    "tags": ["Active", "Region A"], // resolved property tags
    "score": "8 (high)",            // resolved score
    "innerContent": ""              // see limitations
  }
}
```

Use `filterAvailableActions` to narrow by category/lever:

```liquid
{% assign actions = available_actions | filterAvailableActions: "Ultra Frais" %}
{% for a in actions %}
  <li>{{ a.formatted.label }} — {{ a.original.Tab_8880_met42379 | formatNumber: "0,0.00" }} €</li>
{% endfor %}
```

> **Limitation:** `formatted.innerContent` (server-side Markdoc over facets) is **not** reproduced client-side and is always an empty string. `label`, `tags`, `score` and `original` are available.

***

### 4. Custom filters

#### `extractLabelValue`

Parse an `id||name||image` value. Optional arg: `"name"` | `"id"` | `"image"` (default returns `name`, falling back to `id`).

```liquid
{{ record.Tab_8879_label | extractLabelValue: "name" }}
{{ record.Tab_8879_label | extractLabelValue: "image" }}
```

#### `getRecordLabel`

Given a record object, return the value of its first key ending in `label`.

```liquid
{{ record | getRecordLabel }}
```

#### `formatNumber`

Format a number with a [numeral.js](http://numeraljs.com/) format string.

```liquid
{{ record.Tab_8880_met42379 | formatNumber: "0,0[.]00" | append: " €" }}
```

#### `parseFloat`

Coerce a string to a float (useful before arithmetic).

```liquid
{% assign n = record.Tab_8880_prop1022 | parseFloat %}
```

#### `generateBarcodeUrl`

Generate a barcode image as a base64 PNG **data URL** from a value. Use it as an `<img>` source.

```liquid
<img src="{{ record.Tab_8880_prop876 | generateBarcodeUrl }}" />
```

#### `getSelectedRecords`

Flatten a list of selection entries (`selections` or `all_records`) to their record fields, **with `quantity` merged in**. Optional args `category`, then `bucket` filter by `metadata` (omit to return everything).

```liquid
{# all selected records #}
{% assign items = selections | getSelectedRecords %}

{# selected records in a given category #}
{% assign items = selections | getSelectedRecords: "My Link" %}

{# category + bucket #}
{% assign items = selections | getSelectedRecords: "My Link", "My Link" %}

{% for item in items %}
  {{ item.Tab_8880_prop878 }} — qty {{ item.quantity }}
{% endfor %}
```

#### `getRecordsWithQuantity`

Identical output to `getSelectedRecords` (record fields + `quantity`); intended to be piped from `all_records` to list **every** record with its quantity. Optional `category` / `bucket` args.

```liquid
{% assign items = all_records | getRecordsWithQuantity %}
```

#### `filterAvailableActions`

Filter an `available_actions` array by optional `category` and/or `lever` (entries must match every provided dimension). No args → returned unchanged.

```liquid
{{ available_actions | filterAvailableActions }}
{{ available_actions | filterAvailableActions: "Ultra Frais" }}
{{ available_actions | filterAvailableActions: "Ultra Frais", "Rentrer des codes" }}
```

***

### 5. Choosing the right list

| Goal                                                      | Use                                                                                                                                       |
| --------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| Show what the user **selected** (reacts to the selection) | `selections \| getSelectedRecords`                                                                                                        |
| Show **all** records, selected or not                     | `all_records \| getRecordsWithQuantity` (or `available_actions`)                                                                          |
| Need resolved **label / tags / score** per record         | `available_actions` (`.formatted.*`)                                                                                                      |
| Need the raw cube fields                                  | `.record` / `.original` (underscore-keyed)                                                                                                |
| Need the selected **quantity**                            | any of the above — `quantity` is included on `selections` / `all_records` (and merged by `getSelectedRecords` / `getRecordsWithQuantity`) |

> `record` is always available. `selections`, `all_records` and `available_actions` are populated when the document carries a data layer (templates created from a subscription or fanOut template).

***

### 6. Worked example

```liquid
<!DOCTYPE html>
<html>
  <body>
    <h1>{{ record.Store_name | extractLabelValue: "name" }}</h1>
    <p>Prepared by {{ user.firstName }} {{ user.lastName }}</p>

    {% assign items = selections | getSelectedRecords %}
    {% if items.size > 0 %}
      <table>
        <thead><tr><th>Product</th><th>Qty</th><th>Price</th></tr></thead>
        <tbody>
          {% for item in items %}
            <tr>
              <td>
                <img src="{{ item.Tab_8880_prop876 | generateBarcodeUrl }}" />
                {{ item.Tab_8880_prop878 | extractLabelValue: "name" }}
              </td>
              <td>{{ item.quantity | default: 0 }}</td>
              <td>{{ item.Tab_8880_met42379 | formatNumber: "0,0[.]00" | append: " €" }}</td>
            </tr>
          {% endfor %}
        </tbody>
      </table>
    {% else %}
      <p>No items selected.</p>
    {% endif %}
  </body>
</html>
```
