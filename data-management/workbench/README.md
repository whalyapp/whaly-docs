# 🛠 Workbench

## What can I do with the Workbench?

The main objectives of the workbench is to let you:

1. Check the content of your data
2. Filter out the rows that shouldn't be visible in your reports
3. Create new columns to clean or enrich existing columns

### 👩‍✈️ Check the content of your data

To build a proper exploration, the first step is to locate the columns and tables in which your data lives.&#x20;

In order to navigate into your data, you can:

* Scroll both vertically (see more rows) and horizontally (see more columns)
* Click on a column name to see its type
* Click on any cell to see the full detail of the row it belongs to on a panel on the right
* Click on "Hide columns" in order to keep only the relevant columns on your screen

![Workbench](<../../.gitbook/assets/image (49).png>)

### 👌 Filter out the rows that shouldn't be visible in your reports

Some rows shouldn't be visible into your Exploration. Ex. Deleted rows, old rows, bad rows, etc.

With the "Filter" button, you can create a filter to remove bad rows from your exploration.

{% hint style="warning" %}
Filtered rows won't be visible anymore into your Exploration.&#x20;

Meaning that all charts done within Whaly 🐳 or in external BI system won't be able to report on those lines anymore and could be affected by a change of filtering rule.
{% endhint %}

![Filtering rows in the workbench](<../../.gitbook/assets/image (50).png>)

### 🐣 Create new columns to clean or enrich existing columns

Sometimes the raw data isn't enough to measure what you want and you might want to clean or modify the raw data before measuring it. Whaly allows you to add new column easily by clicking on the "Add Column" button.&#x20;

![Adding a new column](<../../.gitbook/assets/image (51).png>)

Whaly offers three types of columns:

#### 1. Formulas

Allow you to create a new column using our formula builder.&#x20;

![adding a formula](<../../.gitbook/assets/image (54).png>)

[Formulas reference can be found here.](formulas.md)

#### 2. Lookup

Allow you to get any column for data that are related in a one to one relationships. For instance, a contact can have only one owner in Hubspot, therefore, you can use a lookup to get any owner info and bring it back on the contact.

{% hint style="danger" %}
You cannot lookup a formula field
{% endhint %}

![Adding a lookup](<../../.gitbook/assets/image (52).png>)

#### 3. Rollup

Allow you to count or sum any numeric columns that are related in a one to many relationship to the current dataset. For instance a contact can be associated with many deals, therefore I can get the total number of deals associated to my each Contact by using a rollup.

![Adding a rollup](<../../.gitbook/assets/image (53).png>)

{% hint style="danger" %}
Column names must only contain alphanumeric characters and you must use underscores instead of spaces. Make sure your column does start by a letter. A column name must be unique on a dataset
{% endhint %}

&#x20;&#x20;
