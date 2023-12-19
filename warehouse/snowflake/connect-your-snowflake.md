# Connect your Snowflake

Setting up the Snowflake warehouse connector involves setting up Snowflake entities (warehouse, database, schema, user, and role) in the Snowflake console, and configuring the Snowflake Warehouse connector using Whaly UI.

This page describes the step-by-step process of setting up the Snowflake warehouse connector.

### Prerequisites[​](https://docs.airbyte.com/integrations/destinations/snowflake/#prerequisites) <a href="#prerequisites" id="prerequisites"></a>

* A Snowflake account with the [ACCOUNTADMIN](https://docs.snowflake.com/en/user-guide/security-access-control-considerations.html) role. If you don’t have an account with the `ACCOUNTADMIN` role, contact your Snowflake administrator to set one up for you.

## Step 1: Set up Whaly-specific entities in Snowflake​ <a href="#step-1-set-up-airbyte-specific-entities-in-snowflake" id="step-1-set-up-airbyte-specific-entities-in-snowflake"></a>

To set up the Snowflake warehouse connector, you first need to create Whaly-specific Snowflake entities (a warehouse, database, schema, user, and role) to read data into Snowflake, track costs pertaining to Whaly, and control permissions at a granular level.

You can use the following script in a new [Snowflake worksheet](https://docs.snowflake.com/en/user-guide/ui-worksheet.html) to create the entities:

1. [Log into your Snowflake account](https://www.snowflake.com/login/).
2. Edit the following script to change the password to a more secure password and to change the names of other resources if you so desire.
3. Execute the script as an `ACCOUNTADMIN` user (check on the top right corner of the Worksheet interface).

{% hint style="info" %}
**Note:** Make sure you follow the [Snowflake identifier requirements](https://docs.snowflake.com/en/sql-reference/identifiers-syntax.html) while renaming the resources.
{% endhint %}

```sql
-- Set variables (these need to be uppercase)
set whaly_bi_username = 'WHALY_BI_USER';
set whaly_bi_password = 'you_should_change_me';

-- This shouldn't be modified
set whaly_bi_role = 'WHALY_BI_ROLE';
set whaly_bi_warehouse = 'WHALY_BI_WAREHOUSE';

begin;

-- create Whaly roles
use role securityadmin;
create role if not exists identifier($whaly_bi_role);
grant role identifier($whaly_bi_role) to role SYSADMIN;

-- create Whaly user
create user if not exists identifier($whaly_bi_username)
password = $whaly_bi_password
default_role = $whaly_bi_role
default_warehouse = $whaly_bi_warehouse;

grant role identifier($whaly_bi_role) 
    to user identifier($whaly_bi_username);

-- change role to sysadmin for warehouse / database steps
use role sysadmin;

-- create Whaly warehouse
create warehouse if not exists identifier($whaly_bi_warehouse)
-- set the size based on your dataset
warehouse_size = medium
warehouse_type = standard
auto_suspend = 120
auto_resume = true
initially_suspended = true
statement_timeout_in_seconds = 600;

-- grant Whaly Warehouse access
grant USAGE
    on warehouse identifier($whaly_bi_warehouse)
    to role identifier($whaly_bi_role);

-- create Private Whaly database (used for SQL queries schema inference)
create database if not exists WHALY_PRIVATE;

grant USAGE
    on database WHALY_PRIVATE
    to role identifier($whaly_bi_role);

create schema if not exists WHALY_PRIVATE.SQL_SCHEMA_INFER;

grant USAGE, CREATE VIEW
    on schema WHALY_PRIVATE.SQL_SCHEMA_INFER
    to role identifier($whaly_bi_role);

commit;
```

## Step 2: Set up Snowflake as a Warehouse in Whaly <a href="#step-3-set-up-snowflake-as-a-destination-in-airbyte" id="step-3-set-up-snowflake-as-a-destination-in-airbyte"></a>

Navigate to the Whaly UI to set up Snowflake as a destination. You can authenticate using username/password.

#### Account ID

The Account ID as an URL. Ex. [`https://xxxxxxx-yyyyyyy.snowflakecomputing.com`](https://xxxxxxx-yyyyyyy.snowflakecomputing.com) . It can be found in Snowflake web UI in **Admin > Accounts** and then you cal click on the 🔗 icon next to the account name in the table.

#### User

The username you created in Step 1 to allow Whaly to access the database. Example: `WHALY_BI_USER`

#### Password

The password associated with the business intelligence user.

## How to get the Snowflake Account URL?

#### If you have a standard Snowflake edition

1. Go on the bottom right part of you screen and open your Account Selector.
2. On the tooltip, select the proper account and click on "Copy account URL"

<figure><img src="../../.gitbook/assets/Screenshot 2022-10-25 at 12.34.17.png" alt=""><figcaption></figcaption></figure>

#### If you have a multi cluster Snowflake edition

1. Go into the "**Admin > Account**" panel on the right side of the screen
2. Next to your account name, click on the 🔗 icon which will copy the URL on your clipboard!

![](<../../.gitbook/assets/Screenshot 2022-08-03 at 11.10.22.png>)
