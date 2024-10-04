# Connect your Databricks

In order to connect your Databricks instance, Whaly needs some credentials. This guide will details the necessary steps:

1. Getting your SQL Warehouse JDBC URL
2. Creation of a Personal Token

### Prerequisites <a href="#prerequisites" id="prerequisites"></a>

To connect Databricks to Whaly, you need the following:

* A Databricks Workspace with SQL support (premium and enterprise plans)
* A SQL Warehouse
* Admin rights on the Databricks Workspace

## Getting your SQL Warehouse JDBC URL

In order to connect to your Databricks Workspace, Whaly will need a SQL Warehouse and its JDBC URL:

* Go your Workspace home page
* In the left panel, select "SQL" to enter the SQL space of your Workspace

<figure><img src="../../.gitbook/assets/image (4) (3).png" alt=""><figcaption></figcaption></figure>

* Once in the SQL space, click on "SQL Warehouses" in the left panel

<figure><img src="../../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

* In the SQL Warehouses screen, either create a dedicated Warehouse or select an existing one

<figure><img src="../../.gitbook/assets/image (14) (1).png" alt=""><figcaption></figcaption></figure>

* Once in a Warehouse, click on "Connection details" tab and copy the JDBC URL

<figure><img src="../../.gitbook/assets/image (3) (1) (1).png" alt=""><figcaption></figcaption></figure>

## Creation of a Personal Token

In order to authenticate on your Databricks Workspace, Whaly needs to have a "Personal Token". In order to create one, please [follow this guide.](https://docs.databricks.com/dev-tools/auth.html#pat)

You can either create a Personal Token on an existing user (simpler way) or create a Service principals and create the Personal Token on it (more secure way but requires doing manual API calls for setup).
