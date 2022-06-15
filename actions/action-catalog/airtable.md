# Airtable

## Why syncing data to Airtable?

This action allow you to sync a chart data back to Airtable. You can then work and distribute your data as it was a native Airtable data.

## What does it look like?

{% hint style="info" %}
This action is only compatible with **Questions**.
{% endhint %}

This action will **append** record to an existing table within an existing database.

Your chart has to share the same columns names as your target Airtable destination table for the integration to work.

## How does it work?

As prerequisite, you need an Airtable account with a database already created.

### Getting your Airtable API key

In order to get your API key please go to [https://airtable.com/account](https://airtable.com/account) and copy your API Key as seen on the screenshot below:

![Your Airtable API Key](<../../.gitbook/assets/image (181).png>)

### Getting your database Id

In order to get your database id please open your database. Click on `Help` at the top right hand corner and then on `API Documentation` at the bottom of the panel. You should be redirected to your table API Documentation.&#x20;

From here you should see your database id as shown on the screenshot below:

![Your database id](<../../.gitbook/assets/image (193).png>)

### Getting your table id

On the same page as previously scroll to the table you wish to copy your data on, and copy your table id. (You can also use the table name)

{% hint style="info" %}
Please note that in order for your action to work, you need to have your columns name the same way as the dimensions and metrics that have been used in your chart. Their type must also match Whaly's types.
{% endhint %}

![Your table name](<../../.gitbook/assets/image (191).png>)
