---
description: How to visualize your reports into Google Data Studio
---

# Connect Whaly to Google Data Studio

This guide will show you the first steps to visualise Whaly reports into Google Data Studio by adding and authorising the Whaly Google Data Studio connector.

&#x20;This will create what is called a **data source** that can be added to your Data Studio reports.

1\. Go to [datastudio.google.com](https://datastudio.google.com/) and log in with your Google account, if needed.

2\. In the top left corner, go to **Create → Data source**.

![](../../.gitbook/assets/image.png)

3\. Scroll down to the Partner Connectors section and look for the **Whaly** connector. Alternatively, you can use the search bar at the top. Click on the connector.

![](<../../.gitbook/assets/image (1).png>)

4\. Click on the **AUTHORIZE** button to give permission to the connector to access your Google account.

![](<../../.gitbook/assets/image (2).png>)

5\. A pop-up will ask you to log in with your Google account – select the same account you use Data Studio with and click on **Allow** to accept the access request.

![](<../../.gitbook/assets/image (3).png>)

6\. Click on the second **AUTHORIZE** button to log in to Whaly.

7\. On Whaly app, please enter your **Whaly credentials** and allow Google Data Studio app by clicking on "**Allow**"

![](<../../.gitbook/assets/image (4).png>)

8\. Select the **Whaly report** that you want to visualise.

![](<../../.gitbook/assets/image (5).png>)

* If you belong to multiple Whaly organisations, you'll be asked to select an organisation. Pick the organisation in which your report is published to continue.

{% hint style="warning" %}
If you do not find your Whaly report in the list, please make sure that you **Published** it in Whaly.
{% endhint %}

9\. You can also update the name of the data source file to something informative, for example based on the selected account(s).

* By default, the data source file will always be "Whaly", a good name would be the report name.

![](<../../.gitbook/assets/image (6).png>)

10\. In the top right corner, click on **CONNECT** to save the configuration as a new data source file.

![](<../../.gitbook/assets/image (7).png>)

11\. You will be taken to the field list, where you can see all available dimensions and metrics of your data source file.

{% hint style="info" %}
By default, you don't need to do anything here.
{% endhint %}

![](<../../.gitbook/assets/image (8).png>)

### **Your data source file has now been created!** 🎉

You can directly start using the data source in a new report by clicking on **CREATE REPORT** in the top right corner of the field list.

![](<../../.gitbook/assets/image (9).png>)

You can now also select it as a data source in your existing reports:

![](<../../.gitbook/assets/image (10).png>)

{% hint style="info" %}
&#x20;If you need more help creating reports or have any other questions about Google Data Studio, feel free to write to us directly on [support@whaly.io](mailto:support@whaly.io).
{% endhint %}
