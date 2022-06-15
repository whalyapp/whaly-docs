# 🔌 Connect your Sources

## **Why syncing my sources to** [**Whaly**](https://whaly.io)**?**

Syncing your data sources can be useful for several reasons

* One cannot improve what one cannot measure
* Centralise data to obtain one source of truth for your operations
* Be able to measure metrics and efficiency from more than one tool
* Analyse your business processes and operations as funnel across different functions / sources
* Automate data ingestion, transformation and reports
* Align your teams performance and achievements

## How sources are working?

When connecting a source to Whaly, you'll pass your credentials to Whaly through a form or a login flow.

Once the credentials passed to Whaly, the connector will go to 3 stages:

* **Authentication**: We'll make sure that the credentials you passed are valid and that we can connect to your Data source
* **Initial load**: We'll sync all the historical data of your Data source. Depending on the volume of data, it can take less than 1 min or some hours.
* **Running**: Every hour, the connector will sync the changes done during the last hour
