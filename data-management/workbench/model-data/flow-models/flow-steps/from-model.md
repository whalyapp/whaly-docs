# From Model

## What does it do?

It allows you to reference the output of another model in your Flow, bringing you composition capabilities without a headache.

## How to use it?

You simply use it by dragging and dropping any previously created **Model** (SQL or Flow) in the **View Selector.**

<figure><img src="../../../../../.gitbook/assets/Screen Cast 2022-09-08 at 3.05.26 PM.gif" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Note: A model cannot reference itself
{% endhint %}

## How to configure it?

There are no configuration option for this step.

## Rendered SQL

If the model is not materialized in your warehouse:

```sql
SELECT * FROM (<IMPORTED MODEL SQL>)
```

If the model is materialized in your warehouse as a view or a table we run:

```sql
SELECT * FROM database.schema.table
```
