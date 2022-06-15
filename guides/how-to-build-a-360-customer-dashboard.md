---
description: >-
  Do you have a lot of customer data spread across your internal tools? Follow
  this guide to discover Whaly's best practices to centralise all this data in a
  single dashboard.
---

# 🔍 How to build a 360° customer dashboard

**Objective:** Understanding your customer's activity throughout your entire business can be a difficult task, as  data is always spread across different tools such as a CRM, an analytics solution, a support software, and so on.

As a data analyst working with Business Developers, Customer Success Managers and Support Specialists, you probably need to answer these questions :&#x20;

* What is the total revenue of our customer **Acme Corp**?&#x20;
* What usage **Acme Corp** had on our software?
* How many conversations did **Acme Corp** had with our support team?&#x20;
* ...

This implementation guide will give you the keys to build a single interactive dashboard that will answer these questions for each one of your customers. You will also learn how to structure your explorations in order to make the most of it.

## A bit of background

In this guide, we will work as a data analyst for :office: Jaffle Soft, a SaaS company. We will build a dashboard used by our team to follow metrics about:

* **Hubspot**, your CRM software
* **Intercom**, your support tool
* **Segment**, your analytics solution

Our dashboard will be able to filter its metrics on our customers and will show the following charts:&#x20;

* The lifetime value by customer
* The number of conversations opened by customer
* The number of login by customer

## High level plan

1. Creating our explorations and charts
   1. &#x20;Hubspot
   2. Segment & Intercom
2. Filtering our dashboard
   1. Adding a customer filter
   2. Adding a date Filter
   3. Using our dashboard

## 1. Creating our explorations and charts

When we build a dashboard, the first thing we need to do is build the explorations. When working with disparate tables and objects, the rule of thumb is:

{% hint style="info" %}
Create one exploration for each table that is used as a metric in a dashboard
{% endhint %}

This rule helps us make sure that we always have the most precise (and complete) data we want to measure at the topmost part of your exploration.&#x20;

Then, we will need to find on a "CustomerID" field on all the explorations that we'll build and declare it as a Dimension. If your systems don't already share a common CustomerID for each customer, you can use the email address to start with.&#x20;

In our example, we'll work with the user email that is shared accross Hubspot, Intercom and Segment.

### 1. 1. Focus on Hubspot

We will start with the first chart : **Total customer revenue by customer.** Breaking down this sentence we can deduce the total amount spend is the metric we will measure, and customer is the dimension we will need to filter on.&#x20;

In Hubspot, two data tables are of interest :&#x20;

* `Deals`, which contains the amount of our won deals&#x20;
* `Contacts` which contains our user emails, used as the CustomerID

Let's start our explorations with the Deals table :&#x20;

* Create a new metric, a cumulative sum of the column "amount".
* Add related data from the `Contacts` table
* Add `date` and `email` as dimensions

![](<../.gitbook/assets/hubspot exploration.gif>)

Now create a timeserie chart using:&#x20;

* Number of Hubspot deals as a metric
* Deal date as time field

And add this timeserie to a new report.

![](<../.gitbook/assets/timeserie hubspot.gif>)

### 1.-2. Segment & Intercom

Let's use Intercom data to create our chart, **the number of conversations opened by customer** :

* Add `date` and `user_email` as dimensions.
* Create a metric, measuring the `Number of Intercom Conversations`
* Use the `date` dimension as time.

Add this metric our report :&#x20;

![](<../.gitbook/assets/image (230).png>)

Now lets do the same thing for Segment in order to calculate **the number of login by customer** :

![](<../.gitbook/assets/image (249).png>)

## 2. Filtering our dashboard

Our dashboard is almost done, but it currently shows data for all of our users, and without the possibility to select a date range.

### 2.2. Adding a customer filter

In order to filter by user email, things are also pretty easy. On the dashboard, click on edit, add a filter and select `email` under `Hubspot - Contacts`. Then, in the "Tiles to update" tab, select the `email` field from Intercom and Segment based explorations.&#x20;

![](<../.gitbook/assets/customer filter.gif>)

### 2.1. Adding a date filter

Since all our metrics have set time field, adding a Date filter is straightforward. On the dashboard,  click on edit, add a filter and select "Default time field". That's it, all our charts will now be based on the range selected in the filter.

### 2.3 Using our dashboard

![](<../.gitbook/assets/using filters.gif>)

That's it: our dashboard shows metrics for our whole customer base, and also allows us to view our data customer per customer :tada:
