# 🔌 Connect your Sources

## **What are Whaly connectors?**

Whaly connectors are a set of managed ETL connectors that can be plugged on your SaaS / Database applications and replicate their Data into your Warehouse.

This can be helpful to help you add quickly new data sources in your Data project without having to go for another ETL vendor.

{% hint style="info" %}
The use of Whaly connectors is **optional**.&#x20;

If your Warehouse already contains data that you want to report on, Whaly can directly connect to it directly.

If some Data Sources are not supported by Whaly connectors, please check the [Data Connector catalog to find a Vendor that can help you move your data.](https://connectorcatalog.com/)
{% endhint %}

### **Supported Warehouses**

Currently, the Whaly connectors supporting those Warehouses:

* BigQuery
* Snowflake

{% hint style="info" %}
If you need Whaly to replicate your SaaS / Database data into other Warehouses, please shoot us an email at support\[at]whaly.io
{% endhint %}

## How sources are working?

When connecting a source to Whaly, you'll pass your credentials to Whaly through a form or a login flow.

Once the credentials passed to Whaly, the connector will go to 3 stages:

* **Authentication**: We'll make sure that the credentials you passed are valid and that we can connect to your Data source
* **Initial load**: We'll sync all the historical data of your Data source. Depending on the volume of data, it can take less than 1 min or some hours.
* **Running**: Every hour, the connector will sync the changes done during the last hour
