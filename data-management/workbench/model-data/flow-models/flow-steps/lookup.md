# Lookup

## What does it do?

Searches down a column of a dataset for a key and returns the value of a specified column in the row found. Think of it as the VLOOKUP from excel but at scale.

## How to use it?

In order to use the lookup step, click on the **Add Column** button and then **Lookup**&#x20;

<figure><img src="../../../../../.gitbook/assets/Screen Cast 2022-09-08 at 6.13.43 PM (2).gif" alt=""><figcaption><p><strong>Add a lookup</strong></p></figcaption></figure>

****

## How to configure it?

<figure><img src="../../../../../.gitbook/assets/image (25).png" alt=""><figcaption><p>Configuring lookup</p></figcaption></figure>

To configure a lookup you need two datasets at least in your canvas. Select the dataset you want to lookup the value from in the dropdown (in order to help you locate the dataset on the canvas it must be blinking when hovered on the dropdown). Then select the column that will be the output of the lookup (the one you want the value to be displayed) and finally select the keys that will be used to identify how the lines should be merged.

In the example above we want to display the `campaign_id` value coming from another dataset under the name of  `new_campaign` on lines that matches `campaign_id` _=_ `customer_id`

