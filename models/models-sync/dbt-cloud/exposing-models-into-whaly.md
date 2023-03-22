# Exposing models into Whaly

By default, when synchronising your dbt Cloud project with Whaly, you won't see any models appearing in the workbench.

This is because most of your models and sources managed in dbt should not be exposed in your Business Intelligence as those are really the fundamental building blocks of your modelling data structure. You want to expose in your consumption layer only the most prepared and enriched models.

In order to expose a model or a source into Whaly, you'll need to flag them in your dbt project directly by adding a specific meta.

## Exposing a model

In the YAML definition of the model, please add the following meta to make it available in Whaly:

```yaml
meta:
    expose_in_whaly: true
```

Here is an example:

```yaml
version: 2

models:
    - name: jaffle_customers
      meta:
        expose_in_whaly: true # <===
      description: "A transformed version of customers through dbt"
      columns:
          - name: customer_id
            description: "The primary key for this table"
            tests:
                - unique
                - not_null
```

## Exposing a source

In the YAML definition of the source, please add the following meta to the source **and to all tables** that you want to expose to make it available in Whaly:

```yaml
meta:
    expose_in_whaly: true
```

Here is an example:

```yaml
version: 2 
sources: 
  - name: "jaffle_shop" 
    schema: "jaffle_shop"
    meta:
      expose_in_whaly: true # <===
    freshness: 
      warn_after: 
        count: 12 
        period: "hour" 
      error_after: 
        count: 24 
        period: "hour" 
    loaded_at_field: "_whaly_synced" 
    tables: 
      - name: "customer" 
        identifier: "customer"
        description: "A person who buys goods or services from a Jaffle shop."
        meta:
          expose_in_whaly: true # <===
        columns:
        - name: customer_id
          description: This is a unique identifier for a customer
          tests:
            - unique
            - not_null
        - name: first_name
          description: Customer's first name. PII.
        - name: last_name
          description: Customer's last name. PII.
```
