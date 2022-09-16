# Cache

Any datasets managed in Whaly has several properties that manage its performance. You can materialize the datasets as table to make complex query run smoother [(read about materialization)](../model-data/materialization-beta.md#materialize-as-table) and you can also manage the way Whaly will update its cache when user query data on this particular dataset from the workbench. In order to better understand how cache is working on Whaly you can [read more here](../../../technical-deep-dive/caching.md#cache-implementation).

## Why do we use cache?

We pride ourselves into providing a great experience to all data consumer in getting query result fast. Moreover, we don't want your datawarehouse bill to go through the roof when your adoption grows. That's why we give you means to control how your cache is working to make the best use of it.

## Managing the cache strategy

In order to manage the cache strategy, please **open any dataset** on the workbench and click on **Information**, then you can find a **Cache Strategy** card with your card option. Please note that by default all dataset created from Whaly's sources will have the cache strategy set up to use the `_whaly_synced` column that is automatically created. Otherwise datasets will be created with a `2 minutes` cache strategy.

<figure><img src="../../../.gitbook/assets/image.png" alt=""><figcaption><p>Editing cache</p></figcaption></figure>

{% hint style="info" %}
Please note that each time you are changing the underlying SQL query or adding/editing new dimensions and metrics to exploration, this also reset the cache.
{% endhint %}

## Understanding  cache options

### Renew cache after a period of time

When this option is selected, every query done on this dataset from an exploration will be kept in cache during the period. If your underlying data change during this period, next queries will not update until the period is over. &#x20;

### Renew cache based on a column value

Each time a query is played we will run the following query:

```sql
select max(COLUMN_NAME) from DATASET_SQL
```

Whenever the data changes, we will drop the cache and renew the query. This is useful when you are plugged directly to tables filled by your ETL as usually they give you insight on when was the last time a query was updated.

### Renew cache based on a sql query

You can also run your own query to get access to your table metadata or more. This allow you  to have more control on how to manage cache.

## Removing cache

There are no straightforward way to remove the cache, but you can write a sql query that always return the current timestamp in order to break the cache for each query.
