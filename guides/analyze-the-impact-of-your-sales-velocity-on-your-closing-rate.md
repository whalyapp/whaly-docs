# ⏰ Analyze the impact of your Sales velocity on your closing rate

**Objective**: The sales momentum don't last as prospects can find alternatives to your product/services pretty fast. Hence, it's important to not stall your Opportunities into a stage of your pipeline, otherwise it can negatively impact your close rate.

However, not all Sales Pipeline are born equal, and all stages are not as time sensitive from the other ones. In order to identify the stages that are the more sensitive to delays, to focus on being reactive during those, it's nice to make an analysis on your historical Opportunities data.

This guide is targeting Hubspot CRM, but the principles can be used with other CRM data.

## **High level plan:**

**a. We'll get the time passed in each stage of your Deal pipeline by each of your deals**

**b. We'll create "buckets" to classify the time spent by each deal in the stages that you want to analyse (ex. "Less than 1 hour", "Less than 1 day", "Less than 1 Month", "Less than 1 Year")**

**c. We'll expose those buckets as "Dimensions" in an Exploration**

**d. We'll create a metric "Close rate" so that we can track your close rate across the different buckets**

**e. We'll create some charts to get insights 🎉**

****

### **a. Get the time passed in each stage for each deal**

Hubspot is giving, for each deal, the time passed in each stage in a Deal property `property_hs_time_in_XXXXXX` with `XXXXXX` being the Stage Id. The column value is the number of milliseconds passed in the stage.

So, to get our analysis done, the first step would be to create a new View on the Hubspot's Deal object and show the columns associated with the Deal Stage that we want to analyse.

{% hint style="info" %}
In order to identify the proper columns, we can have a Look at the \`stage\_id\` column of the Hubspot's Deal Pipeline Stage table.
{% endhint %}

![](<../.gitbook/assets/image (215).png>)

Additionally, we should filter out any deals that have not a value superior at 0 in those columns as those are the Deals that never went through those Stage (they can be from other Pipeline or they could have been lost before entering the Stages that we analyse).

Also, we should filter deals that have `property_hs_is_closed` set at `true` in order to only keep the Deal that are closed, e.g. those that are either Won or Lost.

![](<../.gitbook/assets/image (243).png>)

Finally, we should display the `property_hs_is_closed_won` property. We'll need it to calculate the Close ratio metric later.

### **b. Creating bucket of time**

So, we have the number in milliseconds that deal waited in our Stage, which is great but which is not super helpful to get answers.

In order to get a proper understanding of what time does that represent, we'll create a new column to bucket those time into time period that we can understand.

We can do that by creating a new column in our view with this formula:

```
IF(property_hs_time_in_XXXXXX<3600000;"Less than 1 hour"; IF(property_hs_time_in_XXXXXX<7200000;"Between 1h and 2h"; IF(property_hs_time_in_XXXXXX<86400000;"Between 2h and 1 day"; "More than 1 Day")))
```

The values (1h => 360 000milliseconds, 2h => 7200 000ms, ....) and the labels can be tweaked to match the bucket definition that you want to get for your analysis.

![](<../.gitbook/assets/image (164).png>)

![](<../.gitbook/assets/image (164).png>)

### **c.  Expose those buckets as "Dimensions" in an Exploration**

We should now create a new Exploration from our View created in the previous step. We should create a dimension from the formula column created in the previous step.

![](<../.gitbook/assets/image (186).png>)

**d. We'll create a metric "Close rate" so that we can track your close rate across the different buckets**

In order to create a Close rate metric, we'll firstly 2 metrics: "Number of Closed Deal" and a "`Number of Closed Won Deal`" metric.

![](<../.gitbook/assets/image (231).png>)![](<../.gitbook/assets/image (189).png>)

Then, we create a calculated metric with the formula: `Number of Closed Won Deal / Number of Closed Deal` and we cast it as percent.

![](<../.gitbook/assets/image (262).png>)

**e. We'll create some charts to get insights 🎉**

We can now plot the Close rate per time bucket and get our insights!

![](<../.gitbook/assets/image (179).png>)

### f. Bonus point: Adding a time component

We can add the close date as a Time dimension to see a breakdown of those closing ratio based on the Close time.

This is done by creating a new column in the workbench with the formula:DA

```
DATETIME_FORMAT(property_closedate;"%b %g")
```

And using this new column as the "Close date - Month" in a pivoted chart:

![](<../.gitbook/assets/image (221).png>)
