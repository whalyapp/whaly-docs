# Segment

## **Why syncing my Segment data to** [**Whaly**](https://whaly.io)**?**

Syncing your Segment can be useful for various use cases:

* Track your Users behaviours and your conversion ratios
* Communicate with your Customer Success team the product usage of each of your customer to detect upsells opportunities and churn risks
* Link your product usage data with your CRM and Revenue data to identify correlation and get insights into your offerings
* ...

{% hint style="warning" %}
The Segment connector is only available for the customers using the Manager Warehouse deployment of Whaly.

For customers using [their own data warehouse](broken-reference), please directly [plug your segment instance to your own Warehouse](https://segment.com/docs/connections/storage/warehouses/) and then [import the resulting tables within Whaly.](../../../data-management/workbench/import-tables-from-your-data-warehouse.md)
{% endhint %}

## Which Segment data is synced by [Whaly](https://whaly.io)?

[Whaly](https://whaly.io) 🐳 is currently syncing [the following data.](https://segment.com/docs/connections/storage/warehouses/schema/)

## **Overview**

When creating a Segment connector on Whaly, please go to the connected source and to its settings.

You'll find 4 configurations values that you have to copy paste:

![](<../../../.gitbook/assets/image (201).png>)

Then, go in your Segment instance and follow the steps to add a [BigQuery Warehouse instance to your Segment account.](https://segment.com/docs/connections/storage/catalog/bigquery/#create-the-warehouse-in-segment)

Please make sure to use the Whaly provided credentials when configuring the BigQuery warehouse on Segment interface.
