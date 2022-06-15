# Working with time filtering

When exploring data, it can be handful to be able to filter by date in order to get results only for things that happened this week, last quarter, etc. 🔍

In order to do that, you need to add at least 1 time dimension in your Exploration before exporting it to Google Data Studio ⌛️

{% hint style="info" %}
If there is no time dimension in an Exploration, then it will be impossible to do time filtering on Google Data Studio when connecting 😯

The data displayed on Google Data Studio will be the "all time" data 😃
{% endhint %}

When at least 1 time dimension is detected in the Exploration during the connection to Google Data Studio, an additional setting "**Default Date to filter on**" will appear 🪄

![The last section is about selecting the Date to use for time filtering](<../../.gitbook/assets/image (78).png>)

{% hint style="info" %}
This parameter is **global** for all the charts that will be built using the Data Source, **except if you check the checkbox at the right**, then you will be able to change the Date field to use for time filtering for each chart 👌
{% endhint %}

Once the Data Source is created, you can now add a "**Date range control**" in your reports to configure time filtering.

{% hint style="danger" %}
If you don't have any "Date range control" component on your report but you have a "Default Date to filter on" configured on your Data Source, then **Google Data Studio will automatically apply a filter on the last 28 days 😭**

This can hide some of your data and can be frustrating as there is no visual clue of this implicit filter 🤯

So we **recommend to always have a Date range control component** whenever you are using time dimensions in your Exploration 📅
{% endhint %}

![Menu to add a Date range control](<../../.gitbook/assets/image (79).png>)

And you're done! 🎉

The Date range control will be auto-mapped to the Date field you configured in your Data source 👍
