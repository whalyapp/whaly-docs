# 🗝 Giving access to Snowflake data

By default, the Whaly platform only has access to data that was imported using Whaly connectors.

If you have data already stored inside your Snowflake account that you want to access within Whaly BI, you can do it using the following commands:

{% hint style="info" %}
Please run those commands with the `ACCOUNTADMIN` role to have the proper sharing rights!
{% endhint %}

### 1. Give access to Whaly BI to a Snowflake database

```
set whaly_bi_role = 'WHALY_BI_ROLE';
set snowflake_database = 'INSERT_PROPER_DATABASE_NAME_TO_EXPOSE_IN_WHALY_BI';

grant USAGE
    on database identifier($snowflake_database)
    to role identifier($whaly_bi_role);
```

This will get Whaly access to the database but not to the data stored inside it. Follow the next steps to give access to the proper part of the database to Whaly ⤵️

### 2. Give access to Whaly BI to a Schema and all its Tables located in a Snowflake database (e.g. granular access)

```
set whaly_bi_role = 'WHALY_BI_ROLE';
set snowflake_database = 'INSERT_PROPER_DATABASE_NAME_TO_EXPOSE_IN_WHALY_BI';
set snowflake_schema = 'INSERT_PROPER_SCHEMA_NAME';

USE DATABASE identifier($snowflake_database);
grant USAGE
    on schema identifier($snowflake_schema)
    to role identifier($whaly_bi_role);
grant SELECT 
    on all tables in schema identifier($snowflake_schema)
    to role identifier($whaly_bi_role);
```

### 2bis. Give access to Whaly BI to ALL Schemas and ALL Tables located in a Snowflake database (e.g. wide access)

```
set whaly_bi_role = 'WHALY_BI_ROLE';
set snowflake_database = 'INSERT_PROPER_DATABASE_NAME_TO_EXPOSE_IN_WHALY_BI';

USE DATABASE identifier($snowflake_database);
grant USAGE
    on all schemas in database identifier($snowflake_database)
    to role identifier($whaly_bi_role);
grant SELECT 
    on all tables in database identifier($snowflake_database)
    to role identifier($whaly_bi_role);
```
