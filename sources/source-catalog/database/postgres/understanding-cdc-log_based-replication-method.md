# 💯 Understanding CDC/LOG\_BASED replication method

We use [logical replication](https://www.postgresql.org/docs/10/logical-replication.html) of the Postgres write-ahead log (WAL) to incrementally capture updates and deletes using a replication plugin.

We use `wal2json` as a default plugin, which is included in most Postgres deployments and available from Postgres `9.4+`

### Should I use CDC for Postgres?

* If you need a record of deletions and can accept the limitations posted below, you should to use CDC for Postgres.
* If your data set is small and you just want snapshot of your table in the destination, consider using `FULL_TABLE` Refresh replication for your database instead of CDC.

### CDC Limitations

* Make sure to read our [CDC docs](broken-reference) to see limitations that impact all databases using CDC replication.
* CDC is not available with Heroku Postgres.&#x20;
* Whaly requires a replication slot configured only for its use. Only one source should be configured that uses this replication slot. Instructions on how to set up a replication slot can be found below.
* Log-based replication only works for master instances of Postgres.
* Using logical replication increases disk space used on the database server. The additional data is stored until it is consumed.
  * We recommend setting frequent syncs for CDC in order to ensure that this data doesn't fill up your disk space.
  * If you stop syncing a CDC-configured Postgres instance to Whaly, you should delete the replication slot. Otherwise, it may fill up your disk space.
