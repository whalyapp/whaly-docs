# MariaDB / MySQL

## **Why syncing my MariaDB / MySQL to** [**Whaly**](https://whaly.io)**?**

Syncing your MariaDB / MySQL can be useful for various cases

* Share your product usage with your support and customer success team
* Combine Postgres data with your CRM data to detect churn or upsells
* ....

## Requirements

1. Allow connections from Whaly to your Postgres database by [whitelisting Whaly IPs](../../../sources/whitelisting-whaly-ips.md)

## Configuring the source

The Postgres connector will need the following information:

* **Host**: This should be an IP address or an URL pointing to your Postgres server
* **Port**: This should be the Port of your Postgres, Default to `3306`.
* **User**: This should be the username of a read only Postgres user with read access.
* **Password**: The password associated with the user
