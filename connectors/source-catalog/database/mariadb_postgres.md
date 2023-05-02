# MariaDB / MySQL

## **Why syncing my MariaDB / MySQL to** [**Whaly**](https://whaly.io)**?**

Syncing your MariaDB / MySQL can be useful for various cases

* Share your product usage with your support and customer success team
* Combine MariaDB / MySQL data with your CRM data to detect churn or upsells
* ....

## Requirements

1. Allow connections from Whaly to your MariaDB / MySQL database by [whitelisting Whaly IPs](../../../sources/whitelisting-whaly-ips.md)

## Configuring the source

The MariaDB / MySQL connector will need the following information:

* **Host**: This should be an IP address or an URL pointing to your MariaDB / MySQL server
* **Port**: This should be the Port of your MariaDB / MySQL, Default to `3306`.
* **User**: This should be the username of a read only MariaDB / MySQL user with read access.
* **Password**: The password associated with the user
