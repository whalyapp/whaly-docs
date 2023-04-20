# From your warehouse

## Why importing data from your warehouse

Importing existing tables and views that are already present in your Data Warehouse gives you a great freedom.

It's a great way to:

* Connect with other ETL/ELT systems that creates and feeds tables in your Warehouse ([Segment](https://segment.com/product/warehouses/), [Fivetran](https://fivetran.com/), [Stitch](https://www.stitchdata.com/), [Airbyte](https://airbyte.io/), [Hevo](https://hevodata.com/integrations/pipeline/?source=whaly), in-house connectors, ...)&#x20;
* &#x20;Expose models created with [dbt](https://www.getdbt.com/)
* Expose your ML/AI datasets (scoring, use of ML capabilities of your Warehouse, etc.)

## Import Table from your warehouse

In some case you already have created some tables in your data warehouse that you would like to use in Whaly to create exploration on top of it. To do so you can import raw tables directly into Whaly.  Click on the + button next to **Source** in the **Data Selector** and select **from warehouse**. You'll be prompted to select a name and an icon for your **Source.** A best practice, is to name your source with the name of the schema that you are importing so your users to feel lost.

<figure><img src="../../../.gitbook/assets/Screen Cast 2022-09-08 at 11.41.10 AM.gif" alt=""><figcaption><p>Creating a source for import</p></figcaption></figure>

When your source is created you have the capability to import raw table. To do so click on your newly created source and then on **+ import dataset**. Your are now prompted with a wizard that will help you select:

* The **database** from which you want to import (in BigQuery it is always set as default as BigQuery doesn't have databases)
* The **schema** from which you want to import the tables
* A list of **tables** available in this schema

You can select as much **tables** as you want and click on next.

<figure><img src="../../../.gitbook/assets/Screen Cast 2022-09-08 at 11.41.37 AM.gif" alt=""><figcaption></figcaption></figure>

On the next screen you are prompted with a form that ask you to fill the **dataset** name as well as the **primary keys** so that the import might be finalized. you can click on save and voilà you have imported data from your own warehouse.&#x20;
