# 🗝 Configuring Primary Key of Datasets

When configuring a external Dataset into Whaly, whether it is a Table Import from your Warehouse or when saving a Model (SQL or No-code), you'll have to configure a the set of columns that compose the Primary Key.

Simply put, the Primary Key should be a way to uniquely identify a row in the table. So 2 rows in the table shouldn't have the same values in the columns that are composing the primary key.

#### Example 1:

```
| fruit_id | name     |
|----------|----------|
| 1        | Banana   |
| 2        | Apple    |
| 3        | Orange   |
| 4        | Eggplant |
| 5        | Avocado  |
```

In this table, every row has a different value in the `fruit_id` column. Hence, the `fruit_id` column can be used to uniquely identify all the rows of the table.

Primary Key = `fruit_id` ✅

#### Example 2:

```
| event_date | event_name      | channel    | source       | campaign_id | spend  | 
|------------|-----------------|------------|--------------|-------------|--------|
| 2022-01-01 | Marketing Spend | Search Ads | Google Ads   | 123         | 18.67  |
| 2022-01-01 | Marketing Spend | Search Ads | Google Ads   | 456         | 54.21  |
| 2022-01-02 | Marketing Spend | Search Ads | Google Ads   | 456         | 48.21  |
| 2022-01-01 | Marketing Spend | Social Ads | Facebook Ads | 102212210   | 54.21  |
| 2022-01-01 | Marketing Spend | Social Ads | Facebook Ads | 441215442   | 126.46 |
| 2022-01-02 | Marketing Spend | Social Ads | Facebook Ads | 102212210   | 214.21 |
```

On this example, many columns contains the same value for different rows. Ex. `event_date` column contains multiple times the value "2022-01-01" for different rows.

Same thing for:

* `event_name`
* `channel`&#x20;
* `source`
* `campaign_id`

Hence, those columns **can't be used individually as the Primary Key.**

However, taken all together, `event_date` + `event_name` + `channel` + `source` + `campaign_id` columns are producing a combinaison of values that are unique for each row in the table. If we only keep those columns in the above tables, we have:

```
| event_date | event_name      | channel    | source       | campaign_id |
|------------|-----------------|------------|--------------|-------------|
| 2022-01-01 | Marketing Spend | Search Ads | Google Ads   | 123         |
| 2022-01-01 | Marketing Spend | Search Ads | Google Ads   | 456         |
| 2022-01-02 | Marketing Spend | Search Ads | Google Ads   | 456         |
| 2022-01-01 | Marketing Spend | Social Ads | Facebook Ads | 102212210   |
| 2022-01-01 | Marketing Spend | Social Ads | Facebook Ads | 441215442   |
| 2022-01-02 | Marketing Spend | Social Ads | Facebook Ads | 102212210   |
```

Each row has a unique combinaison of those columns, together they are forming the **Primary Key** 👍

Primary Key = `event_date` + `event_name` + `channel` + `source` + `campaign_id` ✅

### Why is the Primary Key important?

In order for a join to work in an Exploration when having Related Tables, it is necessary to define a **Primary Key** as specified below. It is a requirement when a join is defined so that Whaly can handle row multiplication issues.

Let's imagine you want to calculate`Order Amount` by `Order Item Product Name`.&#x20;

In this case, `Order` rows will be multiplied by the `Order Item` join due to the `hasMany` relationship between `Order` and `Order Item` as it will be a LEFT JOIN.

It is known as the JOIN Fan Out issue.

In order to produce correct results, Whaly will select distinct Primary Keys from `Order` first and then will join these primary keys with `Order` to get the correct `Order Amount` sum result.
