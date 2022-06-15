---
description: >-
  This section helps you understand what explorations are and how you can use
  them to achieve your goals.
---

# 👀 Explorations

### 🙋‍♀️ What are explorations ?

Exploration are a place where you can measure raw data. You can use these measures inside Whaly to get answers quickly on questions you might have or you can use these metrics in our partners connectors such as Google Data Studio.

### 🐣 Getting Started

To create an exploration, click on the left hand menu on the home page and then click on "Create an exploration". Once you are done you should see this screen.

![Creating an exploration](<../../.gitbook/assets/image (37).png>)

An exploration is based on a single dataset you want to explore. Don't worry, you can add related dataset later, but in the end you'll always count the main entity you have selected at this screen.

{% hint style="info" %}
For instance, if you want to count the number of contacts by their company geographic distribution, you would need to create a exploration based on contacts and add the companies afterwards
{% endhint %}

### ❓How to use an exploration

Great, you have created your exploration. Now you can add measures and related data.

![](<../../.gitbook/assets/image (39).png>)

Once inside an exploration you can edit it by clicking on its name at the top of the screen. On the left part of the screen, this is where you will create your measure and connect them to our partners BI tools, on the right part of the screen this is where you  can explore your measures.

If you want to know more about dimension & metrics you can watch this video made by looker that explains very well this concepts:

{% embed url="https://player.vimeo.com/video/287115952" %}

### 🎲 Creating dimensions

In order to view our data, we will create a first dimension. What if we want to view our contacts by first name. In order to do so, click on the "+ " next to contact in the measure section and click on "add a dimension".

![Click on add a dimension](<../../.gitbook/assets/image (40).png>)

Once you have clicked on the button you should see a screen asking you which column you want to use for your dimension. Don't forget that dimensions are like labels, so they work best when the number of values is relatively low (few dozens rather than few hundreds)

![You can select the property\_firstname](<../../.gitbook/assets/image (41).png>)

Click on save. There you go you have created your first dimension. Let's create a metric now.

### 💯 Creating metrics

Metrics allow you to create an operation on a column. The supported operations today are the following:

#### Count

Count the number of line in your dataset. For instance counting the number of line of contacts will be the same as counting the number of contacts

#### Count Distinct

Allow you to select a specific field you want to get the number of distinct value from. For instance if you apply count distinct on the first name of the contact, you will get the number of different first name your contacts have.&#x20;

#### Sum, Average, Min, Max

Allow you to sum a column. Best applied to amounts or prices. For instance you can get your revenue by summing, averaging or getting the min or max of the amount of each deal in your pipeline.&#x20;

**Cumulative Count**

Count function counts a number of items/records that satisfy the given criteria. **** The cumulative count function is the sum of all the counts generated so far.

**Cumulative Sum**

Sum function sums a specific field of items/records that satisfy the given criteria. **** The cumulative sum function is the sum of all the sums generated so far.

When creating a metric you must select an operation and a column.&#x20;

![Creating a metrics](<../../.gitbook/assets/image (42).png>)

#### To go further

When you need to do more complex analysis you can click on the "show advanced" button.&#x20;

![Show advanced section](<../../.gitbook/assets/image (43).png>)

This section allow you to filter your metrics and rename them. For instance if you want to get the number of marketing qualified leads and the number of sales qualified leads, and you have a field call is\_sales\_qualified which can be set to true or false, you can create a metric Count on the Contact dataset and filter it on is\_sales\_qualified equals true to get the number of Sales Qualified Leads. You can filter it to false to get the number of  Marketing Qualified Leads.

### 🔗 Adding related data

Whenever you want to combine data from different datasets you can use related data. In order to do so, click on the "+" button and click on "add related data".

![click on add related data](<../../.gitbook/assets/image (44).png>)

Once you have done that, you should see a menu presenting you with all the dataset related to the one you have selected.&#x20;

![Adding related data](<../../.gitbook/assets/image (45).png>)

Let say that we want to count the number of contact working at a company in a specific domain. Then we want to add Companies as related data to Contact. When doing so we can see that a new table has been added to our exploration and that now I can add dimensions and metrics on companies.

![After adding related data](<../../.gitbook/assets/image (46).png>)

When I count contacts by company domains this will only show me the domain associated to the selected contacts.

### ✅ Validating your data

We have set up our dimensions and metrics, now we want to validate that they makes sense before syncing them to a partner solution. To do so we can use the "Visualize" panel.You can add metrics and dimensions to create the query you want and use the native chart to view your data repartition as well as the breakdown chart to view the underlying data. This panel is also useful to explore your data whenever you have a question.

![Exploring contact by company domains](<../../.gitbook/assets/image (47).png>)



You are all set. If you need to wrangle with your data and create new columns or relationships, please follow the workbench tutorial.



### 🗺 Using maps visualisations

Maps require your data to be formatted using a metric and a dimension. The dimension should contain a list of two letters country code (as per the ISO 3166-1 alpha-2 norm).

Here is an example dataset that can be used for maps :&#x20;

| country\_code | number\_of\_customers |
| ------------- | --------------------- |
| fr            | 12                    |
| us            | 7                     |
| ca            | 3                     |

For more information your can refer to : [https://en.wikipedia.org/wiki/ISO\_3166-1\_alpha-2](https://en.wikipedia.org/wiki/ISO\_3166-1\_alpha-2)
