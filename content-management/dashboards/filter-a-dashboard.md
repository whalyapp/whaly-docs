# Filter a dashboard

In some situation you might want to create slight variations of the same report, for example to change the observed period or the current customer.&#x20;

Instead of creating multiple reports, you can create reports filters to let people filter the data displayed through the tiles of a report.&#x20;

This makes your reports more interactive to end users.

## Adding a filter

To add a filter on a report:

1. Click on the "E**dit**" button in the top right corner
2. Click on "**Add a filter**" button

In the modal that opens, set your filter settings:&#x20;

1. Select the dimension you want to filter on
2. Set a name for your filter
3. Click on create

<figure><img src="../../.gitbook/assets/Screen Cast 2023-05-30 at 12.24.59 PM.gif" alt=""><figcaption></figcaption></figure>

## Updating a filter settings

Filters can be customised in a lot of ways in order to make your dashboard more interactive

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption><p>In edit mode, filters settings are displayed when selecting a filter</p></figcaption></figure>

### Filter settings

* **Name**: the display name of the filter
* **Dimension**: which dimension the filter is based on. When selecting "default time field", the filter will automatically filter charts on their dimension selected as the time.
* **Display filter**: select if you want to hide the filter from the report, preventing users to update the filter value. It is useful when used with [sharing links](../../workspace/sharing-and-collaboration/share-a-report-by-link.md) or with [user attributes](../../user-management/user-attributes.md), in order to give a different default value to a filter based on the sharing link or on the user viewing the dashboard.

### Render options

Render options will be different when the filter is based on a date dimension or not.

#### For time dimensions

* **Defaults to**: can be set to predefined value to select a dimension or user attributes to select the value of a user attribute
* **Default value**: the filter default value

#### For other types of dimensions

* **Filter value**: the displayed dimension value of the filter. Is is used when you want the filter to filter on an id but to display a label instead
* **Filter type**: single value or multiple values
* **Requires a value**: can be set when filter type is "single value"
* **Defaults to**: can be set to predefined value to select a dimension or user attributes to select the value of a user attribute
* **Default value**: the filter default value

### Tiles to update

Select wether a filter should update a specific chart, and on which dimension to apply the filter

### Controlled by

Manage filters that should restrict the autocomplete values of this filter

<figure><img src="../../.gitbook/assets/image (11).png" alt=""><figcaption><p>Example of a controlled filter</p></figcaption></figure>

### **Developer Settings**

You can give an api name to your filter so you can control its value when using the report in [embedded](../../embedding/embedding-api.md#access-your-filters-api-name) mode.
