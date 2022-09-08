# Filter a dashboard

In some situation you might want to create slight variations of the same report, for example to change the observed period or the current customer.&#x20;

Instead of creating multiple reports, you can create reports filters to let people filter the data displayed through the tiles of a report.&#x20;

This makes your reports more interactive to end users.

### Adding a filter

To add a filter on a report:

1. Click on the "E**dit**" button in the top right corner
2. Click on "**Add a filter**" button

In the modal that opens, set your filter settings:&#x20;

1. Select the dimension you want to filter on
2. Set a name for your filter
3. Set a default value for your filter

Then, in the "**Tiles to Update**" tab, select the tiles you want to apply the filter on.

![](<../../.gitbook/assets/customer filter.gif>)

{% hint style="info" %}
When adding new tiles to a report, you should update the tiles to update section on your filters
{% endhint %}

### Hiding filters

When creating or editing filters, you can select the "Hide your filter from the report" option. This will prevent users to change the filter value.

The option is useful when used with [sharing links](share-a-report-by-link.md), in order to give a different default value to a filter based on the sharing link.



### **Developer Settings**

<figure><img src="../../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>

You can give an api name to your filter so you can control its value when using the report in [embedded](../../embedding/embedding-api.md#access-your-filters-api-name) mode.
