# Google Analytics (Universal Analytics)

## **Why syncing my Google** Analytics **to** [**Whaly**](https://whaly.io)**?**

Syncing your Google Analytics can be useful for various cases:

* Consolidate your Google Analytics performance with your others data sources (Facebook Ads, LinkedIn Ads, etc.)
* Track the origin of your traffic (Referral, Paid search, ...)
* Measure the conversion rate of your website
* Monitor the performance of your website/app
* Provide an access on the Google Analytics performance to stakeholders (colleagues, partners, investors) without giving them access to the Google Analytics console
* ...

{% hint style="warning" %}
Our connector is only syncing the [Universal Analytics properties](https://support.google.com/analytics/answer/10220206) of Google Analytics.



For properties that are using [Google Analytics V4](https://support.google.com/analytics/answer/10089681), you should use the [Google Analytics V4 connector.](google-analytics-v4.md)
{% endhint %}

## Which Google Analytics data is synced by [Whaly](https://whaly.io)?

[Whaly](https://whaly.io) 🐳 is currently syncing the following data:

### Referential

* **Account**: An Analytics account is a way to name and organize how you track one or more properties (e.g. websites, mobile apps, point-of-sale devices) using Analytics.
* **Property**: A property is a website, mobile application, or device (e.g. a kiosk or point-of-sale device.)
* **Profile (Views in the UI)**: The view for an Analytics Account is the gateway to the reports: it determines which data from your property appears in the reports.

### Reports

* **Audience Overview**: Give you an overview of when your traffic is visiting your site, how many pages they read and how long they stay.
* **Ecommerce Overview**: Find out what is your ecommerce performance (revenue, etc.).
* **Ecommerce - Product**: Find out what is your ecommerce performance (revenue, etc.).
* **Load Performance**: Give you an overview of your site/app loading performance.
* **Page**: Give you an overview of how your website pages are performing.
* **Traffic origin**: Find out how your users are getting on your site/app.

{% embed url="https://docs.google.com/presentation/d/1g2PNXa5fz9Uhy6opcqpRChYUvI5cwpWMS8isb4sWbFw/edit#slide=id.g244d368397_0_1" %}

[You can find the relationship between all those objects here.](https://docs.google.com/presentation/d/1g2PNXa5fz9Uhy6opcqpRChYUvI5cwpWMS8isb4sWbFw/edit#slide=id.g244d368397\_0\_1)

## How to query Google Analytics data?

Whaly connector is syncing all Analytics Accounts, Properties & Apps and Views of the account selected in the authentication wizard.

In Google Analytics, Reports are attached to Views. When different Views are created on the same Properties & Apps, they're attached reports will contains duplicates.

Hence, when querying the synced reports, it's very important in order to get the proper values to always filter on the "Property/View" objects in order to avoid getting duplicates.&#x20;

{% hint style="success" %}
The field `label` of the View object is recommended to be the field to filter on to get the same results as in Google Analytics.
{% endhint %}

#### Example:

![](<../../../../.gitbook/assets/Screenshot 2022-02-08 at 13.55.53.png>)

Will be equivalent to browsing Google Analytics reports on the "1 Master View"

![](<../../../../.gitbook/assets/image (199).png>)
