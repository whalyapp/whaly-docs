# 🔁 Replication method

A replication method mode governs how Whaly reads from a source and writes to a destination. Whaly provides different replication method to account for various use cases.&#x20;

The easiest way to understand Whaly sync modes is to understand how the modes are named.

1. **Incremental**: Read records added/updated to the source since the last sync job. (The first sync using Incremental is equivalent to a Full Refresh)
   * This is done using a cursor, which will be a field that contains a Date of the record creation / last modification.
2. **Full Table**: Read everything in the source at every sync.

### Full table replication

The **Full table** mode is the simplest methods that Whaly uses to sync data, as it always retrieve all available information requested from the source, regardless of whether it has been synced before. This contrasts with **Incremental sync**, which does not sync data that has already been synced before.

When running a Full Table sync, Whaly will destroy all data in the existing destination table and then pull the new data in. Therefore, data that has been removed from the source after an old sync will be deleted in the destination table.i

{% hint style="info" %}
The "destroy and load" operation is done in a single Warehouse transaction so it is transparent for end users.
{% endhint %}

#### Known limitations

Full table replication method is often longer and will sync more rows than an Incremental replication method. This is because all data is copied during every sync.

For small datasets, this is often not an issue but it can be when starting to deal with high volume of data.

To overcome this limitation, you can switch to an Incremental replication when the connector accept it.

### Incremental replication

When syncing a table **incrementally**, only new or modified data will be synced. Simply put, if you've synced a row before and it has since been updated, this mode will combine the two rows in the destination and use the updated data.

In order to detect which records has been modified since the last sync, a `cursor field` has to be defined. The `updated_at` column in the database is often the `cursor field`

When running queries on the data source, to identify updated records, the connectors are running queries that are equivalent to:

```sql
select * from table where cursor_field > 'last_sync_max_cursor_field_value'
```

{% hint style="info" %}
In most Whaly connectors, the cursor field is pre-defined by the connector itself so you don't have to worry about configuring it.

However, for Databases connectors, the `cursor field` must be properly defined.
{% endhint %}

#### Known limitations

The Incremental replication won't capture "Hard delete", meaning records that have been completly deleted from the data source. This is due to the fact that an "hard delete" is not considered as an update by the data sources so there is nothing to be synced to identify the delete.

In order to overcome this limitation, you can:

* Switch to a Full Table replication method which is capturing deletes
* Go for a "Soft delete" approach in your data source (e.g. deleting records by flagging a `is_deleted` column on the record)
