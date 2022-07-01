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

#### Using custom format

Custom format relies on [numeral.js](http://numeraljs.com/#format) in order to provide you with the ability to easily customise your metrics formatting.

The following table should be read this way:

* Number is an example number
* Format is the format you should type in the custom format input on Whaly
* Output show how your metric will display using the custom format

**Numbers formats**

| Number     | Format     | Output        |
| ---------- | ---------- | ------------- |
| 10000      | 0,0.0000   | 10,000.0000   |
| 10000.23   | 0,0        | 10,000        |
| 10000.23   | +0,0       | +10,000       |
| -10000     | 0,0.0      | -10,000.0     |
| 10000.1234 | 0.000      | 10000.123     |
| 100.1234   | 00000      | 00100         |
| 1000.1234  | 000000,0   | 001,000       |
| 10         | 000.00     | 010.00        |
| 10000.1234 | 0\[.]00000 | 10000.12340   |
| -10000     | (0,0.0000) | (10,000.0000) |
| -0.23      | .00        | -.23          |
| -0.23      | (.00)      | (.23)         |
| 0.23       | 0.00000    | 0.23000       |
| 0.23       | 0.0\[0000] | 0.23          |
| 1230974    | 0.0a       | 1.2m          |
| 1460       | 0 a        | 1 k           |
| -104000    | 0a         | -104k         |
| 1          | 0o         | 1st           |
| 100        | 0o         | 100th         |

**Currency formats**

| Number    | Format      | Output     |
| --------- | ----------- | ---------- |
| 1000.234  | $0,0.00     | $1,000.23  |
| 1000.2    | 0,0\[.]00 $ | 1,000.20 $ |
| 1001      | $ 0,0\[.]00 | $ 1,001    |
| -1000.234 | ($0,0)      | ($1,000)   |
| -1000.234 | $0.00       | -$1000.23  |
| 1230974   | ($ 0.00 a)  | $ 1.23 m   |

**Bytes formats**

| Number        | Format   | Output    |
| ------------- | -------- | --------- |
| 100           | 0b       | 100B      |
| 1024          | 0b       | 1KB       |
| 2048          | 0 ib     | 2 KiB     |
| 3072          | 0.0 b    | 3.1 KB    |
| 7884486213    | 0.00b    | 7.88GB    |
| 3467479682787 | 0.000 ib | 3.154 TiB |

**Percentages formats**

| Number      | Format    | Output   |
| ----------- | --------- | -------- |
| 1           | 0%        | 100%     |
| 0.974878234 | 0.000%    | 97.488%  |
| -0.43       | 0 %       | -43 %    |
| 0.43        | (0.000 %) | 43.000 % |

**Time formats**

| Number | Format   | Output   |
| ------ | -------- | -------- |
| 25     | 00:00:00 | 0:00:25  |
| 238    | 00:00:00 | 0:03:58  |
| 63846  | 00:00:00 | 17:44:06 |

**Exponential formats**

| Number       | Format   | Output   |
| ------------ | -------- | -------- |
| 1123456789   | 0,0e+0   | 1e+9     |
| 12398734.202 | 0.00e+0  | 1.24e+7  |
| 0.000123987  | 0.000e+0 | 1.240e-4 |

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
