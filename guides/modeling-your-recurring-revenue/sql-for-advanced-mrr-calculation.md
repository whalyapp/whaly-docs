# 🐳 SQL for advanced MRR calculation

## SQL for advanced MRR calculation

_Required SQL knowledge:_ WITH clause, MIN, MAX LEAST and COALESCE functions, Window functions, INNER JOINS, CASE statements, BigQuery arrays manipulation, subqueries.

The main differences with the simplified version are:

* Adding inactive months for a customers, between his active subscriptions
* Identifying MRR change for a customer
* Categorising our MRR change between new, renewal, upgrade, downgrade and churn

In order to model our revenue, we will write a query which will execute the following step:&#x20;

1. Retrieve all subscriptions and create a list of all the month between our oldest and most recent subscription dates
2. Calculate our customer revenue by month
3. Create our customer churn months

In the end, our modeled dataset will look like this:&#x20;

![](<../../.gitbook/assets/image (234).png>)

### Retrieve all subscriptions and create a list of all the month between our oldest and most recent subscription dates

This step is the beginning of our SQL for simplified MRR calculate article, which is:&#x20;

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
date_limits AS (
  SELECT 
    MIN(start_date) AS min_date, 
    MAX(end_date) as max_date 
  FROM 
    subscriptions
), 
-- array of month between min and max subscriptions dates
months_array AS (
  SELECT 
    GENERATE_DATE_ARRAY(
      CAST(min_date AS DATE), 
      CAST(max_date AS DATE), 
      INTERVAL 1 month
    ) AS arr 
  FROM 
    date_limits
), 
-- list of months between min and max subscriptions dates
months as (
  SELECT 
    CAST (month as TIMESTAMP) as month 
  FROM 
    months_array, 
    UNNEST(months_array.arr) AS month
),
...
```

### Calculate our customer revenue by month&#x20;

Now for each of our customers we will:

1. Calculate for each customer is first and last active months.
2. Create one row per month between his first and last month.
3. Join our subscriptions with our customer months and set the MRR to 0 for months when a customer subscription is inactive.
4. Identify for each customer the `first_active_month`, `last_active_month`, and for each customer month we add a flag `is_first_month` and `is_last_month`.&#x20;

```sql
...
-- determine when a given customer had its first and last (or most recent) month
customers as (
  select 
    customer_id, 
    min(start_date) as date_month_start, 
    max(end_date) as date_month_end 
  from 
    subscriptions 
  group by 
    1
), 
-- create one record per month between a customer's first and last month
customer_months as (
  select 
    customers.customer_id, 
    months.month 
  from 
    customers 
    inner join months on months.month >= customers.date_month_start 
    and months.month < customers.date_month_end
), 
-- join the account-month spine to MRR base model, pulling through most recent dates
-- and plan info for month rows that have no invoices (i.e. churns)
joined as (
  select 
    customer_months.month, 
    customer_months.customer_id, 
    coalesce(subscriptions.monthly_amount, 0) as mrr 
  from 
    customer_months 
    left join subscriptions on customer_months.customer_id = subscriptions.customer_id 
    and customer_months.month >= subscriptions.start_date 
    and customer_months.month < subscriptions.end_date
), 
customer_revenue_by_month as (
  select 
    *, 
    first_active_month = month as is_first_month, 
    last_active_month = month as is_last_month, 
  from 
    (
      select 
        *, 
        mrr > 0 as is_active, 
        min(case when mrr > 0 then month end) over (partition by customer_id) as first_active_month, 
        max(case when mrr > 0 then month end) over (partition by customer_id) as last_active_month, 
      from 
        joined
    )
),
...
```

### Create our customer churn months&#x20;

We add a new month after our customer last month in order to create one churn month per customer

```sql
...
customer_churn_month as (
  select 
    cast (date_add(cast (month as date), interval 1 month) as timestamp) as month, 
    customer_id, 
    0 as mrr, 
    false as is_active, 
    first_active_month, 
    last_active_month, 
    false as is_first_month, 
    false as is_last_month 
  from 
    customer_revenue_by_month 
  where 
    is_last_month
), 
...
```

### Calculate MRR change

Now we will:

1. Merge our `customer_revenue_by_month` table with our `customer_churn_month` table
2. Get our customer prior month MRR and calculate our current month MRR change

```sql
...
unioned as (
  select 
    * 
  from 
    customer_revenue_by_month 
  union all 
  select 
    * 
  from 
    customer_churn_month
), 
-- get prior month MRR and calculate MRR change
mrr_with_changes as (
  select 
    *, 
    mrr - previous_month_mrr as mrr_change
  from 
    (
      select 
        *, 
        coalesce(
            lag(is_active) over (partition by customer_id order by month),
            false
        ) as previous_month_is_active,
        coalesce(
            lag(mrr) over (partition by customer_id order by month),
            0
        ) as previous_month_mrr,
      from 
        unioned
    )
),
...
```

### Classify our MRR change into categories

Now we have all the data we need to categorize our MRR change. We can easily identify :&#x20;

* New MRR
* Churned MRR
* Upgrade MRR
* Downgrade MRR
* Reactivation MRR

```sql
...
-- classify months as new, churn, reactivation, upgrade, downgrade (or null)
mrr_with_changes_categories as (
  select 
    *, 
    case
      when is_first_month then 'new'
      when not(is_active) and previous_month_is_active then 'churn'
      when is_active and not(previous_month_is_active) then 'reactivation'
      when mrr_change > 0 then 'upgrade'
      when mrr_change < 0 then 'downgrade'
    end as change_category, 
    least(mrr, previous_month_mrr) as renewal_amount 
  from 
    mrr_with_changes
) 
...
```

### Assembling the full query

Now we can assemble all the blocks into our full query:

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
date_limits AS (
  SELECT 
    MIN(start_date) AS min_date, 
    MAX(end_date) as max_date 
  FROM 
    subscriptions
), 
-- array of month between min and max subscriptions dates
months_array AS (
  SELECT 
    GENERATE_DATE_ARRAY(
      CAST(min_date AS DATE), 
      CAST(max_date AS DATE), 
      INTERVAL 1 month
    ) AS arr 
  FROM 
    date_limits
), 
-- list of months between min and max subscriptions dates
months as (
  SELECT 
    CAST (month as TIMESTAMP) as month 
  FROM 
    months_array, 
    UNNEST(months_array.arr) AS month
), 
-- determine when a given customer had its first and last (or most recent) month
customers as (
  select 
    customer_id, 
    min(start_date) as date_month_start, 
    max(end_date) as date_month_end 
  from 
    subscriptions 
  group by 
    1
), 
-- create one record per month between a customer's first and last month
customer_months as (
  select 
    customers.customer_id, 
    months.month 
  from 
    customers 
    inner join months on months.month >= customers.date_month_start 
    and months.month < customers.date_month_end
), 
-- join the account-month spine to MRR base model, pulling through most recent dates
-- and plan info for month rows that have no invoices (i.e. churns)
joined as (
  select 
    customer_months.month, 
    customer_months.customer_id, 
    coalesce(subscriptions.monthly_amount, 0) as mrr 
  from 
    customer_months 
    left join subscriptions on customer_months.customer_id = subscriptions.customer_id 
    and customer_months.month >= subscriptions.start_date 
    and customer_months.month < subscriptions.end_date
), 
customer_revenue_by_month as (
  select 
    *, 
    first_active_month = month as is_first_month, 
    last_active_month = month as is_last_month, 
  from 
    (
      select 
        *, 
        mrr > 0 as is_active, 
        min(case when mrr > 0 then month end) over (partition by customer_id) as first_active_month, 
        max(case when mrr > 0 then month end) over (partition by customer_id) as last_active_month, 
      from 
        joined
    )
), 
-- row for month *after* last month of activity
customer_churn_month as (
  select 
    cast (date_add(cast (month as date), interval 1 month) as timestamp) as month, 
    customer_id, 
    0 as mrr, 
    false as is_active, 
    first_active_month, 
    last_active_month, 
    false as is_first_month, 
    false as is_last_month 
  from 
    customer_revenue_by_month 
  where 
    is_last_month
), 
unioned as (
  select 
    * 
  from 
    customer_revenue_by_month 
  union all 
  select 
    * 
  from 
    customer_churn_month
), 
-- get prior month MRR and calculate MRR change
mrr_with_changes as (
  select 
    *, 
    mrr - previous_month_mrr as mrr_change
  from 
    (
      select 
        *, 
        coalesce(
            lag(is_active) over (partition by customer_id order by month),
            false
        ) as previous_month_is_active,
        coalesce(
            lag(mrr) over (partition by customer_id order by month),
            0
        ) as previous_month_mrr,
      from 
        unioned
    )
), 
-- classify months as new, churn, reactivation, upgrade, downgrade (or null)
mrr_with_changes_categories as (
  select 
    *, 
    case
      when is_first_month then 'new'
      when not(is_active) and previous_month_is_active then 'churn'
      when is_active and not(previous_month_is_active) then 'reactivation'
      when mrr_change > 0 then 'upgrade'
      when mrr_change < 0 then 'downgrade'
    end as change_category, 
    least(mrr, previous_month_mrr) as renewal_amount 
  from 
    mrr_with_changes
) 
select 
  month, 
  customer_id, 
  mrr, 
  mrr_change, 
  change_category 
from 
  mrr_with_changes_categories
```

Run the query and save it (you can use a combination of month and customer\_id as primary key).

### Build the exploration and the dashboard

By creating an exploration on top on this dataset, we will be able to build the following dashboard:

![](<../../.gitbook/assets/image (259).png>)
