# 🧞♂ Import Tables from your Data Warehouse

{% hint style="warning" %}
Importing tables and views from your Warehouse is only possible when you use [your own Warehouse.](broken-reference)

When using a Warehouse managed by Whaly, only tables and views created by [Whaly connectors](../../sources/source-catalog/) are accessible and you can't import any custom tables/views.
{% endhint %}

Importing existing tables and views that are already present in your Data Warehouse gives you a great freedom.

It's a great way to:

* Connect with other ETL/ELT systems that creates and feeds tables in your Warehouse ([Segment](https://segment.com/product/warehouses/), [Fivetran](https://fivetran.com/), [Stitch](https://www.stitchdata.com/), [Airbyte](https://airbyte.io/), [Hevo](https://hevodata.com/integrations/pipeline/?source=whaly), in-house connectors, ...)&#x20;
* &#x20;Expose models created with [dbt](https://www.getdbt.com/)
* Expose your ML/AI datasets (scoring, use of ML capabilities of your Warehouse, etc.)

## Why importing your own Tables and Views

When you start growing your data stack or when dealing with an already existing stack, you start using different tools for the data collection, transformation, governance, etc. and this means creating curated Tables and Views in your Data Warehouse.

Exposing them in Whaly means giving access to them to end users that can start [exploring](../explorations/) those datasets to create insights!

## &#x20;Import an existing Table / View into Whaly

On the [workbench](./) on the "Dataset panel" on your left, open any source and click on "Add Dataset".

![Click on Add Dataset](<../../.gitbook/assets/image (188).png>)

On the Dataset type selector, select "**Import a Dataset**":

![](<../../.gitbook/assets/image (204) (1) (1).png>)

Fill the required fields:

* **Dataset Name**: The name of the Dataset as you want it to appear on Whaly
* **Database**:  Database from your Data Warehouse in which your table / view is stored
* **Schema**: Schema from your Data Warehouse in which your table / view is stored
* **Table**: Table / View in which your data is stored
* **Primary** Key: List of fields that uniquely identify each row

![](<../../.gitbook/assets/image (207) (1).png>)

Click on "Create" and you're done! 🎉
