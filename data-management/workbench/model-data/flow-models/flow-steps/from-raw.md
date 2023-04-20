# From Raw

## What does it do?

It allows you to use raw data that is either imported from your warehouse or that has been replicated through sources.&#x20;

## How to use it?

You simply use it by dragging and dropping any imported **Datasets** (Third Party or Warehouse) in the **View Selector.**



<figure><img src="../../../../../.gitbook/assets/Screen Cast 2022-09-08 at 3.16.19 PM.gif" alt=""><figcaption><p>Import data</p></figcaption></figure>

## How to configure it?

There are no configuration option for this step.

## Rendered SQL

We run:

```sql
SELECT * FROM database.schema.table
```



