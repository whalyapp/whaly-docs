# Rollup

## What does it do?

Searches down a column of a dataset for a key and returns the selected aggregation of the value of a specified column in all rows found.

## How to use it?

In order to use the lookup step, click on the **Add Column** button and then **Rollup**&#x20;

<figure><img src="../../../../../.gitbook/assets/Screen Cast 2022-09-08 at 6.32.11 PM.gif" alt=""><figcaption><p>Add Rollup</p></figcaption></figure>

## How to configure it?

<figure><img src="../../../../../.gitbook/assets/image (1) (2).png" alt=""><figcaption><p>Configuring Rollup</p></figcaption></figure>

To configure a roll you need two datasets at least in your canvas. Select the dataset you want to rollup the value from in the dropdown (in order to help you locate the dataset on the canvas it should be blinking when hovered on the dropdown). Then select the column that will be the output of the rollup as well as the aggregation type (the one you want the value to be displayed) and finally select the keys that will be used to identify how the lines should be merged.

In the example above we want to display the sum of`conversions`  coming from another dataset under the name of  `new_campaign` on lines that matches `campaign_id` _=_ `customer_id`
