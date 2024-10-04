---
description: >-
  This document aims to provide users with a clear understanding of the two
  query modes available in our BI system: Direct Query and Serving Layer.
  Understanding these query modes will help you optimise
---

# ✳️ Query Mode

**Whaly BI supports 2 different Query Modes when running queries to load Dashboards:**

* Direct Query (default)
* Serving Layer

Both Query Mode are providing a different set of advantages and drawbacks and should be chosen based on your specific needs. This document should help you understand their difference and which one do you need for your use cases.

***

**1. Direct Query:**

**Overview:** Direct Query mode refers to a query execution strategy where all queries are routed directly to the Data Warehouse (BigQuery, Snowflake, etc.). This means that every time you interact with the BI dashboards and request data, the system directly accesses the underlying data stored in the Data Warehouse.

**Key Features:**

* **Real-Time Data Access**: Queries are executed directly on the live data stored in the Data Warehouse, ensuring that you always have access to the most up-to-date information.

**Considerations:**

* **Performance**: Direct Query mode may experience slower query performance compared to the Serving Layer, especially when dealing with small datasets.
* **Cost**: Directly querying the Data Warehouse can incur higher costs, particularly if the Data Warehouse platform is expensive in terms of processing and storage (ex. Snowflake).

**Best Use Cases:**

* Clickstream real-time analytics and reporting requirements.
* Ad-hoc analysis where access to the latest data is critical.
* Large datasets that can be efficiently handled by the Data Warehouse.

**2. Serving Layer:**

**Overview:** Serving Layer mode involves copying data from the Data Warehouse into a separate database optimized for query processing managed inside Whaly platform. This database serves as a dedicated layer for running queries done on the BI dashboards, reducing the load on the Data Warehouse and potentially lowering costs.

**Key Features:**

* **Cost-Effective Query Processing**: By offloading queries to a separate database, Serving Layer mode can reduce the cost associated with querying the Data Warehouse, particularly in platforms like Snowflake.
* **Improved Query Performance**: The Serving Layer database is optimized for query processing, leading to faster query execution times compared to Direct Query mode in some scenarios.

**Considerations:**

* **Data Latency**: As data needs to be copied from the Data Warehouse to the Serving Layer database, there may be a slight delay in accessing the most recent data.
* **Limit on the volume of Data**: Only tables up to 5 Go can be copied inside the Serving Layer. Larger data volumes can't be loaded at the moment. When working with large data volume, a pre-aggregation of the data is encouraged to obtain smaller datasets that can be loaded in the Serving Layer.

**Best Use Cases:**

* Periodic reporting and analysis where near real-time data access is not critical.

## Configuring the Query Mode

The configuration of the Query Mode is done directly on the Exploration settings page inside the Workbench. When going in the "_Information_" panel, you can see the current mode used for queries made against this Exploration and change it if needed.

<figure><img src="../.gitbook/assets/image (4) (5).png" alt=""><figcaption><p>Serving Layer</p></figcaption></figure>

<figure><img src="../.gitbook/assets/image (19).png" alt=""><figcaption><p>Direct Query</p></figcaption></figure>

#### Configuring the Query Mode

By clicking on the "Edit" button, you can access the configuration settings of the Query Mode.&#x20;

No configuration is needed for Direct Query.

When in Serving Layer mode, you have the following parameters:

* Extract every: Day / Hour, give you the ability to either do an extract every hour or once a day. It gives you the ability to compromise between warehouse costs and data freshness requirements.
* Run every (only for Daily extracts): Set the hour at which the extract will be done
* On (only for Daily extracts): Business Days / All Days, give your the ability to disable extracts during the weekends to save costs if needed
* Timezone (only for Daily extracts): Set the timezone in which the extract hour will be done

<figure><img src="../.gitbook/assets/image (21).png" alt=""><figcaption><p>Serving Layer configuration</p></figcaption></figure>
