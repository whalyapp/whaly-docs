# Create a Metric

To create a metric, simply click on the + sign next to the table name in the measure panel of the exploration screen, and click on add a metric. This will open the metric creation screen.&#x20;

![](<../../../.gitbook/assets/image (204).png>)

### Select an aggregation type

When creating a metric you must select an operation and a column to perform the aggregation on. Whaly supports the following aggregations:

| Aggregation                             | Description                                                                                                                                                                                                                             |
| --------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <h4>Count</h4>                          | Count the number of line in your dataset. For instance counting the number of line of contacts will be the same as counting the number of contacts                                                                                      |
| <h4>Count Distinct</h4>                 | Allow you to select a specific field you want to get the number of distinct value from. For instance if you apply count distinct on the first name of the contact, you will get the number of different first name your contacts have.  |
| <h4>Sum, Median, Average, Min, Max</h4> | Allow you to sum a column. Best applied to amounts or prices. For instance you can get your revenue by summing, averaging or getting the min or max of the amount of each deal in your pipeline.                                        |
| **Cumulative Count**                    | Count function counts a number of items/records that satisfy the given criteria. **** The cumulative count function is the sum of all the counts generated so far.                                                                      |
| **Cumulative Sum**                      | Sum function sums a specific field of items/records that satisfy the given criteria. **** The cumulative sum function is the sum of all the sums generated so far.                                                                      |

You can also add a filter to your metric in order precisely defined which lines should be included/excluded from your metric (for example, you could set a filter to product\_type equals vegetable to only count products that are vegetables)

### Format your metric

The second step will ask you to select a format for your metric. You can set a custom prefix or suffit (useful for currency, weight, ...), or you can take things a step further by [using the custom format](using-custom-formatting.md) feature.

![](<../../../.gitbook/assets/image (205).png>)

### Give a name and description to your metric

Finally, you should give a name and a description to your metric. This is useful to keep your work clean and understandable for the viewers.

![](<../../../.gitbook/assets/image (186).png>)

When you're done, click on create an your metric will appear in the measures panel.
