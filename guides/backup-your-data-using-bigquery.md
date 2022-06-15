# 📦 Backup your data using BigQuery

**Objective:** in this guide we will learn how to configure BigQuery in order to create daily data backups. This might prove useful if you want to keep an history of your tools data, like your CRM or finance software.

**Prerequisite**: in oder to follow this guide, you will need to have an admin access to the google.

## Backup a table using BigQuery :&#x20;

### 1. Enable the BigQuery data transfer API&#x20;

The first thing we will need to do is enable the BigQuery data transfer API. This allows to schedule queries on a regular basis.

In order to activate the service:

1. Head over to the API page [https://console.cloud.google.com/apis/api/bigquerydatatransfer.googleapis.com/metrics](https://console.cloud.google.com/apis/api/bigquerydatatransfer.googleapis.com/metrics)
2. Click on "Enable API"

{% hint style="info" %}
There might be some propagation delay before this service is seen as activated for Google BigQuery
{% endhint %}

### 2. Create a new dataset in BigQuery

Now we will need to create a new dataset in BigQuery:&#x20;

1. Open the BigQuery Console
2. Create a new dataset in your desired project&#x20;
   1. Give it a name, for example if we want to backup our `jaffle_shop` __ dataset, we will name it __ `jaffle_shop_backup`
   2. Set the region to the same one as your initial table
   3. Click on create
3. Create a table in the new dataset
   1. Give it a name, for example if we want to backup our `customer` __ table, we will name it __ `customer_history`
   2. Click on create

![](<../.gitbook/assets/image (202).png>)

### 3. Write the backup query

Let's write the query that we will use to backup our table:

* In the BigQuery console, open the table you want to backup
* Click on "Query"
* You should now see a Query looking like the following&#x20;

```sql
SELECT FROM "whaly-temp-migration-guide.jaffle_shop.customer"LIMIT 1000
```

* Edit it in order to remove the limit, select every columns in our table and add a new column named `snapshot_ts` that will be populated with the backup timestamp. The final query should look like

```sql
SELECT *, @run_time as snapshot_ts FROM "whaly-temp-migration-guide.jaffle_shop.customer"
```

### 4. Schedule the backup

Now we will add our query to the scheduler:

* Click on Schedule -> Create a new scheduled query
* Give it a name
* Set the schedule according to your needs
* Set the dataset and table to the ones created during step 2
* Set Append to table under Destination table write preference: this will tell BigQuery to create a full backup of the table each day
* Click on save 💾

### 5. Verify the query execution

Now that our query is scheduled, we should check that it's running correctly:&#x20;

* Open the schedule query panel from the left menu bar: [https://console.cloud.google.com/bigquery/scheduled-queries?project=whaly-temp-migration-guide](https://console.cloud.google.com/bigquery/scheduled-queries?project=whaly-temp-migration-guide)
* Check that your query is listed in the summary table
* If you see any error, follow google debugging info to fix them

![](<../.gitbook/assets/image (257).png>)

That's it :tada:
