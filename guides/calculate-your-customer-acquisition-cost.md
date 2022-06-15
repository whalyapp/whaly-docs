# 🎉 Calculate your Customer Acquisition Cost

**Objective**: Getting new customers is hard and require a lot of Marketing and Sales efforts. Being sure that those costs are kept in control and that your acquisition strategy is sustainable is a matter of life and death of your company.&#x20;

This core metric will be looked at by your future investors and stakeholders and should be improved until it reaches a level aligned with your business model. It is a good reporting metric for your Sales & Marketing teams.&#x20;

&#x20;This guide is targeting Facebook Ads, Google Ads and Hubspot CRM, but the principles can be used with other acquisition sources and CRM tools.

Required sources:

a. Marketing sources such as Google Ads, Facebook Ads, LinkedIn Ads or Airtable / Google Sheets (for offline marketing costs)

b. Your CRM or any data source containing your customers and the date they came from the Marketing channel

## High level plan

**a. We'll make sure that each new customers can be linked to a specific Day of acquisition**&#x20;

**b. We'll use a "Day" table to bridge your acquisition tools cost reports with your CRM performance report**

**c. We'll create an exploration that will link together all the Marketing and CRM tables**

**d. We'll create calculated metrics to track your Customer Acquisition Cost, ROAS and other key marketing metrics**

{% hint style="info" %}
In this guide, in order to bridge the Marketing tools (Google Ads, Facebook Ads, etc.) and the Sales tools (Hubspot, Salesforce, Pipedrive), we will use the time as being the link between those system.&#x20;

We do this because in most organisations there is no "Common ID" between the Spent reports coming from the Marketing tools and the CRM tools.

If you're having such IDs in your data setups (ex. Campaign Ids), you can use those to bridge your Marketing data with your Sales data.
{% endhint %}

### **a. We'll make sure that each new customers can be linked to a specific Day of acquisition**&#x20;

Firstly, you need to define, within your CRM, on which day each of your customers were acquired thanks to a Marketing tool. The easiest way of doing it is by using the CRM Contact "Creation Date" if your CRM is only used by your Sales team.

If you have a more complicated acquisition strategy, you can also decide to chose the date when your Contact became "Sales Qualified Leads (SQL)".

Once you have identified the date column you wish to use as the "acquisition date" in your tables, you need to round it up to the Day granularity to be sure it map properly with your Marketing Spend reports.

You can do that by creating a new formula field in the Workbench with:

```
COHORT(property_createdate; "day")
```

![](<../.gitbook/assets/image (165).png>)

**b. We'll use a "Day" table to bridge your acquisition tools cost reports with your CRM performance report**

We'll now create Relationships between the "Day" table and both the Marketing tools and the CRM data.

{% hint style="info" %}
Whaly includes a "Day" table in your Workbench by default to help you combine multiple data sources on time
{% endhint %}

In the "**Day**" object, add one **`Has Many`** relationship per Table on the different Day columns, as follows:

![](<../.gitbook/assets/image (244).png>)

### **c. We'll create an exploration that will link together all the Marketing and CRM tables**

You can now create an exploration that starts from the Day table:



Click on the + icon and on "Add Related Data" to add the different tables needed for the Customer Acquisition Cost calculation. You should obtain:

![](<../.gitbook/assets/image (168).png>)

### **d. We'll create calculated metrics to track your Customer Acquisition Cost, ROAS and other key marketing metrics**

On the Day table, click on the + icon to create Calculated Metric "Marketing Spent":

![](<../.gitbook/assets/image (200).png>)

On the Day table, click on the + icon to create Calculated Metric "Customer Acquisition Cost":

![](<../.gitbook/assets/image (205).png>)

**You should now have:**

![](<../.gitbook/assets/image (247).png>)



And now, you can plot your Customer Acquisition Cost metric in time or calculate it over a period of time to track your Marketing performance 🎉
