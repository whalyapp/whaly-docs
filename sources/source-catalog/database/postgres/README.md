# PostgreSQL / Postgres

## **Why syncing my Postgres to** [**Whaly**](https://whaly.io)**?**

Syncing your Postgres can be useful for various cases

* Share your product usage with your support and customer success team
* Combine Postgres data with your CRM data to detect churn or upsells
* ....

## Requirements

1. Postgres `v9.4.x` or above
2. To avoid a critical PostgreSQL bug, use at least one of the following minor versions:
   * PostgreSQL 12.0
   * PostgreSQL 11.2
   * PostgreSQL 10.7
   * PostgreSQL 9.6.12
   * PostgreSQL 9.5.16
   * PostgreSQL 9.4.21
3. Allow connections from Whaly to your Postgres database by [whitelisting Whaly IPs](../../../whitelisting-whaly-ips.md)

## Configuring the source

The Postgres connector will need the following information:

* **Host**: This should be an IP address or an URL pointing to your Postgres server
* **Port**: This should be the Port of your Postgres, Default to `5432`.
* **User**: This should be the username of a read only Postgres user. [You'll find instruction below to create it](./#configuring-a-database-read-only-user)
* **Password**: The password associated with the user
* **Database name**: The name of the database to be synced. In a Postgres server, there can be multiple databases, depending on your setup. If you want to replicate multiple databases, you'll have to create one connector per database.
* **Replication method**: When multiple replication method are available, you should select here the type of replication that you want to use. Supported methods are: "`FULL_TABLE`" and "`LOG_BASED`"

## Choosing a replication mode

Whaly can sync your Postgres database with 2 replication method:

* `FULL_TABLE`: This mode will, at each sync run, copy all your data from all your tables and replace the existing data in Whaly by the new copy. While this replication mode is easy to setup, if your tables contains a lot of rows, sync duration will be long and it'll take some processing power on your database, which can slow down your production system.
* `LOG_BASED` (recommended when supported): This mode will use the [Postgres replication mechanism](https://www.postgresql.org/docs/10/logical-replication.html) of Postgres to only sync the updates of your database at each sync run. This will have a lighter impact on your database but[ it'll require some setup on your part to properly configure it](./#configuring-the-log\_based-replication-method). **Note:** It is also called CDC (Change Data Capture), Logical Replication or WAL Replication.

Support matrix:

| Hosting type                    | FULL\_TABLE | LOG\_BASED                         |
| ------------------------------- | ----------- | ---------------------------------- |
| Generic Postgres (=Self hosted) | ✅ Supported | ✅ Supported after Wal2Json install |
| Google Cloud SQL                | ✅ Supported | ✅ Supported                        |
| Amazon RDS                      | ✅ Supported | ✅ Supported                        |
| Heroku Postgres                 | ✅ Supported | ❌ Not supported                    |

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

## Configuring the `LOG_BASED` replication method

This part of the guide only applies to you if you chose to use the LOG\_BASED replication method. Otherwise, you can skip it.

&#x20;In order to configure a LOG BASED replication, you'll need to:

1. Check that the proper replication plugin is installed on your Postgres server
2. Activate the Replication of your Postgres server (⚠️ will need a database reboot)
3. Give the `REPLICATION` role to the Postgres user you want to use with Whaly
4. Create a Replication Slot

### 1. Replication plugin

We use `wal2json` as a default Postgres Replication plugin. This plugin has to be installed on your Postgres server if you are managing Postgres by yourself. [See here the instruction.](https://github.com/eulerto/wal2json)&#x20;

If you're using Google Cloud SQL or Amazon RDS hosted Postgres, then `wal2json` plugin is already installed on your Postgres server 🎉

### 2. Activate replication on your Postgres server

#### Google Cloud SQL

[You can follow this guide.](https://cloud.google.com/sql/docs/postgres/replication/configure-logical-replication)

#### AWS RDS

Go to the `Configuration` tab for your DB cluster.

1. Find your cluster parameter group. You will either edit the parameters for this group or create a copy of this parameter group to edit. If you create a copy you will need to change your cluster's parameter group before restarting.
2. Within the parameter group page, search for `rds.logical_replication`. Select this row and click on the `Edit parameters` button. Set this value to `1`.
3. Wait for a maintenance window to automatically restart the instance or restart it manually.
4. Finally, [follow the rest of steps above](./#setting-up-cdc-for-postgres).

#### Generic / Self Hosted

[You can follow this guide.](https://www.sqlpac.com/en/documents/postgresql-9.6-10-11-configuration-setup-streaming-replication-standby-ubuntu.html)

### 3. Grant REPLICATION role to the Postgres User

After logging to you Postgres server, you can edit the user created previously to give it access to the logical replication.

```
ALTER USER existing_user WITH REPLICATION;
```

### 4. Create a Replication Slot

After logging to you Postgres server, you should create a replication slot for the database you want to replicate.

```
  SELECT *
  FROM pg_create_logical_replication_slot('pipelinewise_<database_name>', 'wal2json');  
```

Replace the `<database_name>`with the name of the Postgres database that you configure in the source.&#x20;

{% hint style="info" %}
If you want to sync multiple databases from your Postgres server, you'll need to create multiple Replication Slots, one per database.
{% endhint %}



