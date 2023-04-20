# 🏄 Schema drift

Schema drift is the case where an actual table schema in the data source is different from the  schema of the target table in the Warehouse.&#x20;

This is happening when the Data source schema is updated:

* A new column is created
* A column change its type
* A column is deleted

When a Schema is drifting, there is an inconsistency between the Data Source schema and the destination schema.

Whaly connectors are handling such cases to reduce the level of data inconsistencies while ensuring that all analysis / queries made on the destination table in the Warehouse continue to work.

### A new column is created

Whenever a new column is created in the data source, Whaly will create a new column in the destination table in the Warehouse at the next sync.

For "`FULL TABLE`" replicated tables, the new column will be completely filled at the next sync.

For "`INCREMENTAL`" replicated tables, the new column will be filled only for recently updated records at the next sync. A full resync of the table will be necessary to backfill all the records.

### A column change its type

Whenever a column in the data source change its type, ex. String becomes a Number, a new column will be created on the destination table on the warehouse to hold the new values.

Previous values with the previous type will remain untouched in the previous column.

Newly created columns have the following format: `columnName_NEWTYPE`, ex. `amount_eur_STRING`

For "`FULL TABLE`" replicated tables, the new column will be completely filled at the next sync.

For "`INCREMENTAL`" replicated tables, the new column will be filled only for recently updated records at the next sync. A full resync of the table will be necessary to backfill all the records.

### A column is deleted

Whenever a new column is deleted in the data source, Whaly will stop syncing it in the destination table in Warehouse. However, values already synced in the past will remain untouched and can still be read in the Warehouse so existing analysis will keep working.

