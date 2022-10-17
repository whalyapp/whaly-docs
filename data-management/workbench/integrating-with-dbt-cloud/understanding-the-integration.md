# Understanding the integration

## Replication items

The integration will read your manifest.json and replicate the following resources from dbt:

* Models
* Sources
* Tests
* Test results
* Materialization results
* Source freshness results

## Models

Models declare in your dbt project will be created as SQL Models in Whaly. Those models are non editable and the generated SQL query from dbt will be accessible to your analysts. If your model has a test that renders a column uniq, this column will automatically be flagged as the primary key. For models imported from dbt the materialization cannot be edited through the Whaly user interface and must be edited through your dbt project.

If your model has associated test, you can view their results in the preview tab or the information tab.&#x20;

<figure><img src="../../../.gitbook/assets/image (27).png" alt=""><figcaption><p>A tested column with passing test</p></figcaption></figure>

All results associated to your model will be available in the information tab under the Run Result card.

<figure><img src="../../../.gitbook/assets/image (10).png" alt=""><figcaption><p>All tests associated to a dataset</p></figcaption></figure>

Please note that we automatically import your lineage as well

<figure><img src="../../../.gitbook/assets/image (13).png" alt=""><figcaption><p>dataset lineage</p></figcaption></figure>

## Sources

We import your sources as they are defined in your dbt project. The source in your dbt project will create a Source in Whaly and each table as defined under your source will be imported in your Whaly project. This comes with the source freshness as well as any tests associated with your source table. You can't control the emoji associated to your source though.

<figure><img src="../../../.gitbook/assets/image (25).png" alt=""><figcaption><p>Source results</p></figcaption></figure>

## Benefits

### Lifecycle

For any source, model, or test added in your dbt project will be automatically synced on the next period to your Whaly environment, any source, model or test deleted will also be deleted on the next sync. This help you keep up to date and tidy environment.&#x20;

Your analyst can quickly create and iterate on new models in your Whaly environment and when those models are steady enough they can be moved to your dbt environment and replicated in your Whaly instance.

This helps you to get a consistant pace of iteration.

### Lineage Alerts

Since dashboards and exploration lives in Whaly we will display an error on any exploration or charts impacted with a lineage issue. This helps prevent your business users to trust stale data.&#x20;

<figure><img src="../../../.gitbook/assets/image (12).png" alt=""><figcaption><p>Lineage issue</p></figcaption></figure>
