# 🐟 SQL for simplified MRR calculation

## SQL for simplified MRR calculation

_Required SQL knowledge:_ WITH clause, MIN and MAX functions, INNER JOINS, BigQuery arrays manipulation.

In order to model our revenue, we will write a query which will execute the following step:&#x20;

1. Retrieve all subscriptions
2. Calculate oldest and most recent subscriptions dates
3. Generate a list of all the month between our oldest and most recent dates
4. Join our months with our subscriptions

In the end, our modeled dataset will look like this:&#x20;

![](<../../.gitbook/assets/image (217).png>)

### Retrieve all subscriptions

Let's start by querying all of our subscriptions (you may need to update the subscription table in the from command):&#x20;

```sql
-- all subscriptions
with subscriptions as (
  select
    subscription_id,
    customer_id,
    monthly_amount,
    start_date,
    end_date,
  from
    ${TABLES["Subscriptions"]["subscriptions"]}
)
select * from subscriptions
```

Run this query, you should see the content of your subscription table as the result.

### Calculate oldest and most recent subscriptions dates

Then we will need to calculate our  oldest start date and most recent end date. Let's do it using the `min` and `max` functions:

```sql
...
-- min and max subscriptions dates
date_limits as (
  select
    min(start_date) as min_date,
    max(end_date) as max_date
  from
    subscriptions
)
select * date_limits
```

Run this query, you should see the min and max subscriptions dates.

### Generate a list of all the month between our oldest and most recent dates

Now we will generate the list of months between our `min_date` and our `max_date`:

```sql
...
-- array of month between min and max subscriptions dates
months_array as (
  select
    GENERATE_DATE_ARRAY(
      CAST(min_date as DATE),
      CAST(max_date as DATE),
      INTERVAL 1 month
    ) as arr
  from
    date_limits
),
-- list of month between min and max subscriptions dates
months as (
  select
    CAST(month as TIMESTAMP) as month
  from
    months_array,
    UNNEST(months_array.arr) as month
)
select * from months
```

Run this query, you should see the list of months between our `min_date` and `max_date`.

### Join our months with our subscriptions

Let's write the final step, which will use an inner join between our `subscriptions` and our `months` tables in order to generate one line per active subscription month.

The entire SQL query should now be as following:

```sql
-- all subscriptions
with subscriptions as (
  select
    subscription_id,
    customer_id,
    monthly_amount,
    start_date,
    end_date,
  from
    ${TABLES["Subscriptions"]["subscriptions"]}
),
-- min and max subscriptions dates
date_limits as (
  select
    min(start_date) as min_date,
    max(end_date) as max_date
  from
    subscriptions
),
-- array of month between min and max subscriptions dates
months_array as (
  select
    GENERATE_DATE_ARRAY(
      CAST(min_date as DATE),
      CAST(max_date as DATE),
      INTERVAL 1 month
    ) as arr
  from
    date_limits
),
-- list of month between min and max subscriptions dates
months as (
  select
    CAST(month as TIMESTAMP) as month
  from
    months_array,
    UNNEST(months_array.arr) as month
),
-- months joined with active subscriptions months
subscriptions_months as (
  select
    months.month,
    subscriptions.customer_id,
    subscriptions.monthly_amount as mrr,
    subscriptions.start_date,
    subscriptions.end_date
  from
    subscriptions
    inner join months on months.month >= subscriptions.start_date
    and months.month < subscriptions.end_date
)
select
  *
from
  subscriptions_months
```

Run the query: we now have one line per active subscription month :tada:

Save the query (you can use a combination of `month` and `customer_id` as primary key).&#x20;

### Build the exploration and the dashboard

By creating an exploration on top on this dataset, we will be able to build the following dashboard:

![Simplified MRR dashboard](<../../.gitbook/assets/image (197).png>)
