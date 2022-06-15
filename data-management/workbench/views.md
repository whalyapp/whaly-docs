# 🪟 Views

Views are a great way to:

* collaborate in a team 🤜🤛
* share common filters so that everyone can have the same vision 🧐
* iterate on with personal view to not disturb other coworkers while wrangling 🧑🏻‍💻

## Why using views?

When working with the workbench, it is quite common to filter rows and hide columns that are irrelevant for the current analysis to get a better view of the data.

However, this can have consequences for your coworkers who may be needed a different view of your data because they work on a different analysis / question than you.

Hence, Views is a way to, both:&#x20;

* sharing global row filtering and column visibility in public views&#x20;
* giving you the flexibility of creating your personal view to work on your own without any impact to your coworkers.

## How can I use views?

The name of the current view is displayed on the **top left corner** of the workbench:

![Here, we are in "Pierre's view"](<../../.gitbook/assets/image (62).png>)

By clicking on the icon at the left side of the View's name, you open the View panel where you can manage view (list, access, create, delete).

![We have 2 views: "All contact" and "Pierre's view"](<../../.gitbook/assets/image (63).png>)

By clicking on the bottom button "**Create a view**", you can spawn your own view and start working on your own without impacting others.

When creating an exploration or adding related data to an existing exploration, you'll be asked for which View you want to use.

{% hint style="danger" %}
**Filters and column visibility updates** to views that are referenced inside an exploration will be used in the exploration, hence **impacting the results of those explorations**.

We recommend to differentiate:

* **👀 Exploration views** that should be dealt with **carefully** as Explorations / Reporting are based on them so any change to those view can impact metrics / dimensions calculations ⚠️
* **👧 Personal views** that are **only to browse the workbench** and that are safe to update as nothing is dependent of them
{% endhint %}
