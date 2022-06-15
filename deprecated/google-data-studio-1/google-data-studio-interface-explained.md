# Create my first charts

There are various menu available in the Google Data Studio interface. This section focuses on&#x20;

![](<../../.gitbook/assets/image (13).png>)

## Edit mode

![](<../../.gitbook/assets/image (17).png>)

To change and edit a dashboard you must be in "Edit" mode. Click on the "Edit" button on the top right corner of your window

## View mode

To visualize how your report or dashboard looks like you must be in view mode. The view mode is practical for testing how your current page looks and feels as well as changing the dates or the filters should any be defined. To activate the view mode click on the "View" button at the top right corner of your window.

![](<../../.gitbook/assets/image (18).png>)

## Add data

The Add data sub menu is used every time you want to connect a report from Whaly to Google Data Studio.

{% hint style="info" %}
Please follow [this section](https://docs.whaly.io/visualize/google-data-studio-1/google-data-studio) to see how to connect a report from Whaly to Google Data Studio.
{% endhint %}

## Add a chart

The Add a chart menu is where you will have all types of charts. It is one of the most useful menu in Google Data Studio to test various type of charts for one Whaly report.

![](<../../.gitbook/assets/image (14).png>)

### Create and manage a Table

Tables are the best way to explore your data in Google Data Studio. Once selected, you will have to define the zone allocated to your newly created Table.

![](<../../.gitbook/assets/image (15).png>)

Google Data Studio will fill your table automatically with a dimension column (ga_source) and a metric column (_ga\_users).

![](<../../.gitbook/assets/image (16).png>)

To edit, make sure you are on the "Edit mode" (check the beginning of this page under the "Edit mode" section to learn more about it). Then click on the table you will see a specific menu toggling at the right side of your screen.

![](<../../.gitbook/assets/image (19).png>)

This edition menu is broken down into two sections "Data" and "Style".

![](<../../.gitbook/assets/image (20).png>)

Congrats you have created your first chart!

#### Data section

The "Data" section will allow you add dimensions, metrics, edit the data source, sort your data and define a date range. By a simple drag and drop you can easily edit your table depending on what you want to build.

{% hint style="info" %}
If you do not know how to make the difference between dimension and metrics, please consult the [dedicated section](https://docs.whaly.io/visualize/google-data-studio-1/dimensions-metrics).
{% endhint %}

#### Style section

The "Style" section will allow you to customise your chart design.&#x20;

![](<../../.gitbook/assets/image (21).png>)

### Create and manage a Time Series

In order to track the number of sessions over time, I will choose a Time Series.&#x20;

![](<../../.gitbook/assets/image (22).png>)

{% hint style="info" %}
Make sure your Whaly report always contain a date that will be used as a dimension. It is a prerequisite for Time Series.
{% endhint %}

![](<../../.gitbook/assets/image (23).png>)

Should you need to edit the date format click on the edit button on the left side of your date dimension.

![](<../../.gitbook/assets/image (24).png>)

Then pick another date format

![](<../../.gitbook/assets/image (25).png>)

![](<../../.gitbook/assets/image (26).png>)

![](<../../.gitbook/assets/image (27).png>)

Depending on your data and date dimension, Google Data Studio will reshape your graph accordingly.

### Set the displayed date range&#x20;

You can choose to let the default date range be picked when a viewer will see your report. However should you want to set a more specific date range to one chart, you can do so by configuring the "Default date range".

![](<../../.gitbook/assets/image (28).png>)

Click on "Custom" and define a date range.

![](<../../.gitbook/assets/image (29).png>)

Click on the date range on the top right corner or manually set one.

![](<../../.gitbook/assets/image (30).png>)

The top right option will allow you to set a dynamic date range of your choosing

![](<../../.gitbook/assets/image (31).png>)

Select a date range and click on "Apply".

Now we have a good view of users on our landing page and the source of visits

![](<../../.gitbook/assets/image (33).png>)

I will now add specific counters on the top of these two charts. To do so, you can use Scorecards.

### Create and manage Scorecards

Scorecards are extremely helpful to count specific metrics and are generally set up at the beginning of your report.

To add a Scorecard, click on "Add a Chart" and select "Scorecard".

![](<../../.gitbook/assets/image (34).png>)

Here is my scorecard to measure the number of users over the period.

![](<../../.gitbook/assets/image (35).png>)



