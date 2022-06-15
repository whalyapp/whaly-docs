# Add a control / filter

When working on a dashboard / chart, it is often quite useful to give control to the end users on how the data should be filtered.

In Google Data Studio, this is possible through the addition on a report of a "Control".

Those are accessible, when in EDIT mode, in the toolbar:

![](<../../.gitbook/assets/image (75).png>)

Depending on how you want the filter to look like, you can choose which control best suits you.&#x20;

Don't hesitate to test them to be sure that you're not passing by the perfect filter for your use case.

{% hint style="warning" %}
The "time" based fields are **not filterable** using the generic controls (Drop-down list, Fixed-size list, etc.)

[Please refer to our dedicated section about time filtering 🙏](working-with-date-filtering.md)
{% endhint %}

## Configuring controls / filters

{% hint style="info" %}
All controls, except for the Date range ([see our dedicated guide](working-with-date-filtering.md)), can only filter a single Data source.&#x20;

Only the charts based on this Data source will be controlled by the filter.
{% endhint %}

In order to select which Data Source should be filtered and using which field, edit the control component and select:

* the Exploration in the Data Source section
* the field to use for filtering in the "Control field" section

![](<../../.gitbook/assets/image (76).png>)

And you're done 🤗
