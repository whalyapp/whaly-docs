# 💼 Create a sales performance dashboard

**Objective**: Closely following sales performance metrics, such as time to close, conversions rates and average order amount is vital for any business. It is mandatory to have this information when working with investors. It also helps you understand when to accelerate on sales as you notice your metrics are getting better.

In this guide, we will learn how to build a report that will:&#x20;

* Display our average order amount and total revenue
* Track our sales velocity over time
* Monitor our sales pipeline conversions rates

This guide is targeting Hubspot CRM, but the principles can be used with other CRM data.

Here is what we will build :&#x20;

![](<../.gitbook/assets/image (222).png>)

## High level plan:&#x20;

1. Creating our Deal exploration
2. Creating our "new revenue" metric
3. Creating our "average order amount" metric
4. Creating our sales velocity chart
5. Creating our deal conversion funnel
6. Creating our report

### Creating our Deal exploration

Let's start with the easy stuff and create a new exploration. We will start our exploration from our Deal table as we want to see 100% of our deals in our sales dashboard.&#x20;

Let's create the exploration and add the column `property_createdate` as a dimension.

### Creating our "new revenue" metric

In order to display our new revenue, we will want to count the total amount for the deals won. It's easy to create such a metric:&#x20;

* Create a new metric
* Set it to `Sum` of the column `property_amount`
* In the advanced settings, set a filter on `property_dealstage` equals `closedwon`
* Set a suffix to €

### Creating our "average order amount" metric

To display the average order amount, we will will recreate the same metric as for total revenue but we will use the aggregation "average" instead of sum:&#x20;

* Create a new metric
* Set it to be `Average` of the column `property_amount`
* In the advanced settings, set a filter on `property_dealstage` equals `closedwon`
* Don't forget the suffix and the name :nerd:

Now you can use these two metrics on our dashboard:

![](<../.gitbook/assets/image (166).png>)

### Creating our sales velocity chart

Hubspot provides a column named `property_days_to_close` on the deal table which contains the number of days from the deal creation date to the deal closed date. To monitor our sales velocity, we will create a new metric:&#x20;

* Create a new metric
* Set it to average of the column `property_days_to_close`
* In the advanced settings, set a filter on `property_dealstage` equals `closedwon`
* You can add `days` as a suffix in the advanced settings

![](<../.gitbook/assets/image (245).png>)

### Creating our deal conversion funnel&#x20;

In order to closely monitor our sales pipeline, we will create a conversion funnel on top of our sales process. In this guide our funnel is composed of three steps: Demo -> Trial -> Customer

First, we will create a metric for each of our pipeline steps : number of trial done, number of demo done and number of customer. Let's do it:&#x20;

* Create a new metric
* Set it to count
* In the advanced settings, set a filter to on `property_hs_date_entered_in_xxx` to `is set`, where `xxx` is the corresponding stage id in Hubspot.&#x20;
* Give it a name (for example, number of demo done)

{% hint style="info" %}
The matching between the pipeline stage id and the pipeline label (displayed in hubspot) in available in the Deal pipeline stages table.
{% endhint %}

This allows us to monitor our sales funnel by month:&#x20;

![](<../.gitbook/assets/image (224).png>)

As well as displaying our global sales funnel:&#x20;

![](<../.gitbook/assets/image (242).png>)

We will also calculate our conversion rate between our pipeline stage. Here we will need to create two calculated metrics:&#x20;

1. Demo conversion rate, which is `number of trial done / number of demo done`
2. Trial conversion rate, which is `number of customer / number of trial done`

This will allow us to monitor our conversion rates in time:&#x20;

![](<../.gitbook/assets/image (267).png>)

### Creating our report&#x20;

Now we have all the elements we need to build our sales performance report. Let's just assemble everything and apply some formatting to get our final result :&#x20;

![](<../.gitbook/assets/image (232).png>)
