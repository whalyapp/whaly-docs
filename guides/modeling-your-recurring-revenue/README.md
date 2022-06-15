# 💳 Modeling your recurring revenue

**Objectives**:&#x20;

Calculating your recurring revenue (MRR or ARR) is vital for every SaaS and subscription based businesses. It helps understanding your past and current revenue as well as projecting your upcoming revenue. When talking with investors, you will also be asked to share this information, the more detailed the better. Keeping track of your recurring revenue will allow you to monitor your company growth.&#x20;

If you follow this article, you will be able to build the following dashboard:

![](<../../.gitbook/assets/image (209).png>)

## High level plan

* Gathering our required data sources
* Importing our data and creating a SQL dataset
* Writing down the SQL Query (BigQuery)
  * SQL for simplified MRR calculation
  * SQL for advanced MRR calculation

### Gathering our required data sources

Every business is unique, and the way your business handles subscriptions may be slightly different than what this article assumes. Here, we will work with a really simple data source :&#x20;

![](<../../.gitbook/assets/image (258).png>)

As you can see our subscription dataset is very clean, as we have:&#x20;

* One line per subscription, with the monthly amount, the subscription start date and the subscription end date.
* Our subscriptions begin the first day of the month and ends the last day of the month.
* A customer can only have one active subscription during a given month.
* At the end of his subscription, a customer can cancel (churn), downgrade, upgrade or renew his subscription.

The main problem with the current form of this dataset is that it will not play well with visualisation software, i.e. you will not be able to build this kind on charts :&#x20;

![](<../../.gitbook/assets/image (173).png>)

At the end of this article, we will have modeled our date into an analytics-ready dataset, meaning that we will have one line per subscription per active month. We will also take things one step further in order to identify churn, new revenue, renewals, upgrades and downgrades, as well as calculate MRR changes.

### Importing our data and creating a SQL dataset

#### Importing our data into Whaly

{% hint style="info" %}
If you do not have suitable data you can download our example dataset by [clicking here](https://docs.google.com/spreadsheets/d/1jkC63lSUKdVN\_vBN87sW553x2lpFZt-d69x\_ccHjM-M/edit?usp=sharing).
{% endhint %}

Let's import our data into Whaly, you can use the source of your choice in order to do so. If you are just playing around and experimenting, we recommend you use either our Google Sheet connector:&#x20;

{% embed url="https://docs.whaly.io/sources/source-catalog/google-sheets" %}

#### &#x20;Creating a SQL dataset

In order to model our current subscriptions data, we will need to create a SQL dataset. This can easily done in Whaly.

You can create a new source, select the option `From warehouse` and name it `SQL`. Inside this source create a SQL dataset named `Simplified SQL`.

If you have not created any dataset until now, it is easily done by following our documentation:&#x20;

{% embed url="https://docs.whaly.io/data-management/workbench/sql-datasets" %}

### Writing down the SQL Query (BigQuery)

We will see two methods in order to model our MRR:

* A simplified method for SQL intermediates users.
* An advanced method for SQL advanced to expert users.

During these steps by steps we will rely on some specific BigQuery commands in order to manipulate dates. These steps should be adapted if used with an other warehouse.

__
