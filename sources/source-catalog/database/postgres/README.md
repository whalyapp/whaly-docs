# PostgreSQL / Postgres

## **Why syncing my Postgres to** [**Whaly**](https://whaly.io)**?**

Syncing your Postgres can be useful for various cases

* Share your product usage with your support and customer success team
* Combine Postgres data with your CRM data to detect churn or upsells
* ....

## Requirements

1. Postgres `v9.4.x` or above
2. Allow connections from Whaly to your Postgres database by [whitelisting Whaly IPs](../../../../warehouse/postgres/whitelisting-whaly-ips.md)

## Configuring the source

The Postgres connector will need the following information:

* **Host**: This should be an IP address or an URL pointing to your Postgres server
* **Port**: This should be the Port of your Postgres, Default to `5432`.
* **User**: This should be the username of a read only Postgres user. [You'll find instruction below to create it](./#configuring-a-database-read-only-user)
* **Password**: The password associated with the user
* **Database name**: The name of the database to be synced. In a Postgres server, there can be multiple databases, depending on your setup. If you want to replicate multiple databases, you'll have to create one connector per database.

## Configuring a database read only user

Whaly will need a Postgres user in order to connect to your database. We recommend to create a specific user with only Read Only access for the replication.&#x20;

Using Postgres access control features, you'll be able to finely configure which data (tables, columns) should be replicated within Whaly.

Below instructions, executed with a Postgres Admin user, will create a read only user that can be used to sync all tables of your Postgres server.

```
CREATE USER <username> PASSWORD '<some-password>';
GRANT USAGE ON SCHEMA "public" TO <username>;
GRANT SELECT ON ALL TABLES IN SCHEMA "public" TO <username>;
ALTER DEFAULT PRIVILEGES IN SCHEMA "public" GRANT SELECT ON TABLES TO <username>;
```

{% hint style="info" %}
**Note**:

* Replace `<username>` and `<some-password>` by the login and password that you want to give to the read only user used for the replication
* If you're using another SCHEMA that the default `"public"` one in Postgres, please replace `"public"` with your SCHEMA name.
{% endhint %}

## Troubleshooting

#### I got the "Error: terminating connection due to conflict with recovery" message in the logs

When the connector is reading from a Postgres replica that is configured as a Hot Standby, any update from the primary server will terminate queries on the replica after a certain amount of time, default to 30 seconds.&#x20;

This default waiting time is not enough to sync any meaning amount of data. See the `Handling Query Conflicts` section in the Postgres [documentation](https://www.postgresql.org/docs/14/hot-standby.html#HOT-STANDBY-CONFLICT) for detailed explanation.

Here is the typical exception:

```
terminating connection due to conflict with recovery
```

Possible solutions include:

* \[**Recommended**] Set [`hot_standby_feedback`](https://www.postgresql.org/docs/14/runtime-config-replication.html#GUC-HOT-STANDBY-FEEDBACK) to `true` on the replica server. This parameter will prevent the primary server from deleting the write-ahead logs when the replica is busy serving user queries. However, the downside is that the write-ahead log will increase in size.
* \[**Recommended**] Sync data when there is no update running in the primary server, or sync data from the primary server.
* \[**Not Recommended**] Increase [`max_standby_archive_delay`](https://www.postgresql.org/docs/14/runtime-config-replication.html#GUC-MAX-STANDBY-ARCHIVE-DELAY) and [`max_standby_streaming_delay`](https://www.postgresql.org/docs/14/runtime-config-replication.html#GUC-MAX-STANDBY-STREAMING-DELAY) to be larger than the amount of time needed to complete the data sync. However, it is usually hard to tell how much time it will take to sync all the data. This approach is not very practical.
