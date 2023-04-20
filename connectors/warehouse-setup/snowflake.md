# Snowflake

Setting up the Snowflake destination connector involves setting up Snowflake entities (warehouse, database, schema, user, and role) in the Snowflake console, and configuring the Snowflake destination connector using Whaly UI.

This page describes the step-by-step process of setting up the Wahly->Snowflake connectors integration.

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
-- set variables (these need to be uppercase)
set whaly_dataloading_username = 'WHALY_DATALOADING_USER';
set whaly_dataloading_password = 'you_should_change_me';

-- This shouldn't be modified
set whaly_dataloading_role = 'WHALY_DATALOADING_ROLE';
set whaly_dataloading_warehouse = 'WHALY_DATALOADING_WAREHOUSE';
set whaly_dataloading_database = 'WHALY_DATALOADING_DATABASE';
set whaly_bi_role = 'WHALY_BI_ROLE';

begin;

-- create Whaly roles
use role securityadmin;
create role if not exists identifier($whaly_dataloading_role);
grant role identifier($whaly_dataloading_role) to role SYSADMIN;

-- create Whaly users
create user if not exists identifier($whaly_dataloading_username)
password = $whaly_dataloading_password
default_role = $whaly_dataloading_role
default_warehouse = $whaly_dataloading_warehouse;

grant role identifier($whaly_dataloading_role) 
    to user identifier($whaly_dataloading_username);

-- change role to sysadmin for warehouse / database steps
use role sysadmin;

-- create Whaly warehouses
create warehouse if not exists identifier($whaly_dataloading_warehouse)
warehouse_size = xsmall
warehouse_type = standard
auto_suspend = 1800
auto_resume = true
initially_suspended = true;

-- grant Whaly Warehouse access
grant USAGE
    on warehouse identifier($whaly_dataloading_warehouse)
    to role identifier($whaly_dataloading_role);

-- create Whaly data loading database
create database if not exists identifier($whaly_dataloading_database);

-- grant Whaly database access
grant OWNERSHIP
    on database identifier($whaly_dataloading_database)
    to role identifier($whaly_dataloading_role);

grant USAGE
    on database identifier($whaly_dataloading_database)
    to role identifier($whaly_bi_role);

commit;
```

### Step 2: Set up Snowflake dataloading credentials in Whaly <a href="#step-3-set-up-snowflake-as-a-destination-in-airbyte" id="step-3-set-up-snowflake-as-a-destination-in-airbyte"></a>

Navigate to your Warehouse page in the Settings and configure the Dataloading credentials.

| Field                   | Description                                                                                                 |
| ----------------------- | ----------------------------------------------------------------------------------------------------------- |
| Dataloading \| User     | The username you created in Step 1 to allow Whaly to access the database. Example: `WHALY_DATALOADING_USER` |
| Dataloading \| Password | The password associated with the dataloading user.                                                          |

<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>
