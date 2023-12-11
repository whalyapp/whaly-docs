# Connect your Postgres

Setting up the Postgres destination connector involves setting up Postgres entities (user, grants) through Postgres access, and configuring the Postgres destination connector using Whaly UI.

This page describes the step-by-step process of setting up the Postgres destination connector.

### Step 1: Create a Whaly read only user in Postgres​ <a href="#step-1-set-up-airbyte-specific-entities-in-snowflake" id="step-1-set-up-airbyte-specific-entities-in-snowflake"></a>

To set up the Postgres destination connector, you first need to connect to your Postgres server to run some SQL queries.

```sql
CREATE USER whaly_bi WITH ENCRYPTED PASSWORD 'some_password_here';
GRANT CONNECT ON DATABASE database_name to whaly_bi;
\c database_name
GRANT SELECT ON ALL SEQUENCES IN SCHEMA public TO whaly_bi;
GRANT SELECT ON ALL TABLES IN SCHEMA public TO whaly_bi;
```

If you're using a schema other than `public`, run this command to grant usage permissions to Whaly:

```sql
GRANT USAGE ON SCHEMA schema_name TO whaly_bi;
```

To make sure that future tables you add to the public schema are also available to the `whaly_bi` user, run these commands:

```sql
ALTER DEFAULT PRIVILEGES IN SCHEMA public GRANT SELECT ON tables TO whaly_bi;
ALTER DEFAULT PRIVILEGES IN SCHEMA public GRANT SELECT ON sequences TO whaly_bi;
```

Depending on your setup, the preceding commands may need to be altered. If another user or role is creating tables that the `whaly_bi` user needs future permissions for, you must specify a _target_ role or user to apply the `whaly_bi` user's permission grants for:

```sql
ALTER DEFAULT PRIVILEGES FOR USER <USER_WHO_CREATES_TABLES> IN SCHEMA public GRANT SELECT ON tables TO whaly_bi;
ALTER DEFAULT PRIVILEGES FOR USER <USER_WHO_CREATES_TABLES> IN SCHEMA public GRANT SELECT ON sequences TO whaly_bi;
-- or
ALTER DEFAULT PRIVILEGES FOR ROLE <ROLE_THAT_CREATES_TABLES> IN SCHEMA public GRANT SELECT ON tables TO whaly_bi;
ALTER DEFAULT PRIVILEGES FOR ROLE <ROLE_THAT_CREATES_TABLES> IN SCHEMA public GRANT SELECT ON sequences TO whaly_bi;
```

See [`ALTER DEFAULT PRIVILEGES`](https://www.postgresql.org/docs/9.4/sql-alterdefaultprivileges.html) on PostgreSQL's website for more information.

### Step 2: Set up Postgres as a destination in Whaly <a href="#step-3-set-up-snowflake-as-a-destination-in-airbyte" id="step-3-set-up-snowflake-as-a-destination-in-airbyte"></a>

Navigate to the Whaly UI to set up Postgres as a destination. You can authenticate using username/password.

#### Host

The host IP or URL of your Postgres server. It can be a Read-only replica or a regular Postgres server.

#### Port

The Port to be used to connect to Postgres. Default is: `5432`

#### Database

The name of the Postgres database to connect to on the server. Default is: `postgres`

#### User

The name of the user to use for Whaly BI. Default is: `whaly_bi`

#### **Password**

The password of the user created for Whaly BI

### Step 3: Secure the database connection

Please make sure to properly [whitelist Whaly IPs](whitelisting-whaly-ips.md).

