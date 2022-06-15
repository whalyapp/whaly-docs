# 🔎 Drills

Drills are a way of configuring what should be displayed to the end users when they interact with reports by clicking on charts.

It's a great way to:

* Allow your viewers to go beyond just a report aggregated data 🧑‍🚀
* Add more interactivity to the report 🤖

## Why using drills?

When viewers will start consuming your reports, they will have additional questions.&#x20;

> Why are my sales going up or down?&#x20;
>
> What are the deals currently in closed won or lost? etc.&#x20;

To give more flexibility and level of interaction to viewers, you can set up drills in the [Workbench](./) that will then be automatically available to all your charts in the reporting section.

## How can I configure drills?

In the workbench, at the bottom left corner of your window, click on the "**Drills**" button

![](<../../.gitbook/assets/image (156).png>)

From here you can pick any property you want to be available as a Drill in the report.

![](<../../.gitbook/assets/image (157).png>)

On my report, viewers can now drill every deal based on the `deal_name` and the `mrr`.

![](<../../.gitbook/assets/image (158).png>)

On the chart at the center, if I click on the **11,358$ MRR** value, I will then get this drill:

![](<../../.gitbook/assets/image (159).png>)

{% hint style="danger" %}
Drills are configured per [View](views.md) and not globally for an object. If you use multiple [Views](views.md) on your objects, you therefore need to identify the proper [View](views.md) to configure the Drill at the right place.

To do so, follow the guide below ⬇️
{% endhint %}

## Identify the proper View to set up my drill

On the exploration interface, identify the object on which you have configured the [Metric](../../deprecated/google-data-studio-1/dimensions-metrics.md) that people will click on.

![](<../../.gitbook/assets/image (160).png>)

In my case, I wanted to implement a Drill on the **Clients** object. Click on the "..." button and then "**Info**"

![](<../../.gitbook/assets/image (161).png>)

![](<../../.gitbook/assets/image (162).png>)

Here you can see that the [View](views.md) used is "**All Clients**".&#x20;

So, in the [Workbench](./), I will navigate to the **Clients** object and select the "**All Clients**" [View](views.md) before setting up the **Drills**.
