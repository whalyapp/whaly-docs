# Snowflake

Setting up the Persistence Engine for Snowflake involves setting up Snowflake entities (warehouse, database, schema, user, and role) in the Snowflake console.

This page describes the step-by-step process of setting up the Snowflake destination connector.

### Prerequisites[​](https://docs.airbyte.com/integrations/destinations/snowflake/#prerequisites) <a href="#prerequisites" id="prerequisites"></a>

* A Snowflake account with the [ACCOUNTADMIN](https://docs.snowflake.com/en/user-guide/security-access-control-considerations.html) role. If you don’t have an account with the `ACCOUNTADMIN` role, contact your Snowflake administrator to set one up for you.

### Step 1: Set up Whaly-specific entities in Snowflake[​](https://docs.airbyte.com/integrations/destinations/snowflake/#step-1-set-up-airbyte-specific-entities-in-snowflake) <a href="#step-1-set-up-airbyte-specific-entities-in-snowflake" id="step-1-set-up-airbyte-specific-entities-in-snowflake"></a>

To set up the Snowflake destination connector, you first need to create Whaly-specific Snowflake entities (a warehouse, database, schema, user, and role) with the `OWNERSHIP` permission to write data into Snowflake, track costs pertaining to Whaly, and control permissions at a granular level.

You can use the following script in a new [Snowflake worksheet](https://docs.snowflake.com/en/user-guide/ui-worksheet.html) to create the entities:

1. [Log into your Snowflake account](https://www.snowflake.com/login/).
2. Edit the following script to change the password to a more secure password and to change the names of other resources if you so desire.
3. Execute the script as an `ACCOUNTADMIN` user (check on the top right corner of the Worksheet interface).

{% hint style="info" %}
**Note:** Make sure you follow the [Snowflake identifier requirements](https://docs.snowflake.com/en/sql-reference/identifiers-syntax.html) while renaming the resources.
{% endhint %}

```
-- Set variables
set whaly_scratch_database = 'SCRATCH';
set whaly_scratch_schema = 'SCRATCH';

-- This shouldn't be modified
set whaly_bi_role = 'WHALY_BI_ROLE';

begin;

-- change role to sysadmin for warehouse / database steps
use role sysadmin;

-- create Whaly scratch database
create database if not exists identifier($whaly_scratch_database);

-- grant Whaly database access
grant OWNERSHIP
    on database identifier($whaly_scratch_database)
    to role identifier($whaly_bi_role);

-- create scratch schema
use database identifier($whaly_scratch_database);
create schema if not exists identifier($whaly_scratch_schema);

grant OWNERSHIP on schema identifier($whaly_scratch_schema)
	to role identifier($whaly_bi_role);

commit;
```
