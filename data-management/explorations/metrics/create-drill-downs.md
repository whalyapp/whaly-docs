# Create Drill Downs

Drills downs are used by data consumers to explore further a metric. They will be available when the user clicks on the chart and will show the underlying records that have been used to compute the metric.



Drill downs can be defined at the table level or at the metric level. Metric will inherit for the table configuration and can override the table configuration if needed.&#x20;

### Configuring Drill Downs at the table level

<figure><img src="../../../.gitbook/assets/image (235).png" alt=""><figcaption><p>Drill at the table level</p></figcaption></figure>

&#x20;At the table level drill downs can be:

* **Disabled** by default: This means that end users won't be able to click on the chart to get access to the records.
* **Inherit** from the dataset configuration (default): [On the dataset](../../workbench/understanding-datasets/drills.md) that is used to build the table you can define columns that will be used on all metrics
* Use a **combination of dimension and metric**: You can generate your own query with your own dimension and metrics to make the drills more readable

By default all metrics created under this table will inherit the table configuration

### Configuring Drill Downs at the metric level

<figure><img src="../../../.gitbook/assets/image (236).png" alt=""><figcaption><p>Configuring drills at the metric level</p></figcaption></figure>

At the metric level drill downs can be:

* **Disabled:** If for some reason you want to avoid your users to view records on a specific metric, this can be useful for calculated metrics  as record level is not easily understandable.
* **Inherit from table (default):** This will give you the drills that are configured at the table level
* **Select from existing measure**: You can generate any query you wish at the metric level
