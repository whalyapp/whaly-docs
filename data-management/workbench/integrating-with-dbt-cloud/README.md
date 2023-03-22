# 💞 Models sync

{% hint style="info" %}
Whaly offer an [integrated lightweight modelling layer](../model-data/) that can be seem as "conflicting" with others solutions such as dbt, Keboola and Dataform.

However, this is not the case, both type of Models can and should be used at the same time for different reasons, [read this article to understand why.](why-using-dbt-and-whaly.md)
{% endhint %}

Models sync is a set of integrations that enable Whaly to import Models managed by an external modelling solution (dbt Cloud, dbt Core, Keboola, Dataform).&#x20;

Thanks to those integrations, it is possible to surface to Data Consumers all the metadata that were produced in the Modelling layer. This includes:

* Model Documentation import
* Source freshness checks imports
* Models tests results
* Lineage imports

Being able to share those informations with Data consumers by makig it available in Whaly is important to build trust with your stakeholders and make sure that important facts such as pipelines failures are communicated through warnings in the produced Dashboards.

This synchronisation is really helpful when:

a. A dashboard breaks and an analyst is asked to have a look. Having all the modelling information available in Whaly will help them understand what is the issue without having to go back and forth between Whaly and the modelling system. Issues can be resolved more quickly this way.

b. When a pipeline breaks (source sync is late or a data test failed), the Model sync will automatically alerts your data consumers in their dashboards and charts that there is something wrong and prevent them from making bad decisions on top of broken KPIs.

## Understanding the integration

### Models

Models declare in your external modelling solutiom will be created as Models in Whaly. Those models are read only and the generated SQL query will be accessible to your analysts.&#x20;

If your model has a test that renders a column unique, this column will automatically be flagged as the primary key of this model.&#x20;

If your model has associated tests, you can view their results in the preview tab or the information tab.

<figure><img src="../../../.gitbook/assets/image (27).png" alt=""><figcaption><p>A tested column with passing test</p></figcaption></figure>

All results associated to your model will be available in the information tab under the Run Result card.

<figure><img src="../../../.gitbook/assets/image (10) (3).png" alt=""><figcaption><p>All tests associated to a dataset</p></figcaption></figure>

Please note that we automatically import your lineage as well:

<figure><img src="../../../.gitbook/assets/image (13) (4).png" alt=""><figcaption><p>dataset lineage</p></figcaption></figure>

### Sources

We import your sources as they are defined in your modelling project. The source in your modelling project will create a Source in Whaly and each table as defined under your source will be imported in your Whaly project.&#x20;

This comes with the source freshness as well as any tests associated with your source table.

<figure><img src="../../../.gitbook/assets/image (25) (2).png" alt=""><figcaption><p>Source results</p></figcaption></figure>

## Benefits

### Lifecycle

For any source, model, or test added in your modelling project will be automatically synced on the next period to your Whaly environment, any source, model or test deleted will also be deleted on the next sync. This help you keep up to date and tidy environment.&#x20;

Your analyst can quickly create and iterate on new models in your Whaly environment and when those models are steady enough they can be moved to your modelling environment and replicated in your Whaly instance.

This helps you to get a consistant pace of iteration.

### Lineage Alerts

Since dashboards and exploration lives in Whaly we will display an error on any exploration or charts impacted with a lineage issue. This helps prevent your business users to trust stale data.&#x20;

<figure><img src="../../../.gitbook/assets/image (12) (3).png" alt=""><figcaption><p>Lineage issue</p></figcaption></figure>
