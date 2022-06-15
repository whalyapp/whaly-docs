---
description: >-
  This guide aims at explaining how to embed a report in salesforce on the home
  page or on a specific object page.
---

# ☁ Embedding reports in Salesforce

In order to embed Whaly reports in Salesforce, you need to:

* Be an developer on your Salesforce org
* Have at least a report created in your Whaly instance

## Setting up your Salesforce org

First of all you need to create the necessary component in your salesforce org to embed Whaly. In order to speed up the process we have created a git repository with all the code required to embed Whaly.&#x20;

{% embed url="https://github.com/whalyapp/salesforce-embed" %}

## Adding your app to your home or object page

In order to add your newly created app to your home page or record page, you should navigate to the page you wish to embed your report on and click on settings and edit page as shown below.

![Embeding Whaly](<../.gitbook/assets/image (253).png>)

Once you are on the edition menu you can drag and drop the WhalyEmbed app and enter your credentials as show below.

![Page builder](<../.gitbook/assets/image (216).png>)

## Forwarding context to your report

By default the app that we created on salesforce pass three filters

* userId: Contains the connected user ID from Salesforce
* userEmail: Contains the connected user email from Salesforce
* recordId: When displaying your report on a record page you will get the current recordId otherwise you should expect it to be null

Therefore on Whaly side you can set up filters with a api name to either userId, userEmail, or objectId to take advantage of those prebuilt features.

## To go further

You can read our documentation on how our embedding mechanism works there:

{% embed url="https://docs.whaly.io/data-management/reports/embed-a-report" %}

Learn how to deploy a lightning app

[https://developer.salesforce.com/docs/atlas.en-us.236.0.apexcode.meta/apexcode/apex\_debug\_test\_deploy.htm](https://developer.salesforce.com/docs/atlas.en-us.236.0.apexcode.meta/apexcode/apex\_debug\_test\_deploy.htm)

[\
](https://developer.salesforce.com/docs/atlas.en-us.236.0.apexcode.meta/apexcode/apex\_debug\_test\_deploy.htm)
