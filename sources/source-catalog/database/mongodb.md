# MongoDb

## **Why syncing my MongoDb to** [**Whaly**](https://whaly.io)**?**

Syncing your MongoDb can be useful for various cases

* Share your product usage with your support and customer success team
* Combine MongoDb data with your CRM data to detect churn or upsells
* ....



## Requirements

1. MongoDB database versions `2.6+` or above
2. MongoDB Atlas database versions `4.0+`
3. Allow connections from Whaly to your Postgres database by [whitelisting Whaly IPs](../../whitelisting-whaly-ips.md)

## Configuring the source

The MongoDb connector will need the following information:

* **Host**: This should be a URL pointing to your MongoDB server
* **Database name**: The name of the database to be synced. In a MongoDB server, there can be multiple databases, depending on your setup. If you want to replicate multiple databases, you'll have to create one connector per database.
* **Replication method**: When multiple replication method are available, you should select here the type of replication that you want to use. Supported methods are: "`FULL_TABLE`" and "`OPLOG_BASED`"

Please note that the user we use to connect to your mongo instance will need to have access to the `local` database in order to read the `oplog.`

## What is being synced

We sync the content of your collections. As MongoDb is Document based database we then pack each document in your collection in the following format:

&#x20;

| key - STRING     | value - JSON                            |
| ---------------- | --------------------------------------- |
| Your document ID | a JSON representation of your document  |
