# 🚀 Push

With **Push**, you can configure an [Action](actions/) on your **Dashboards** or **Questions**. Once configured, Push can be either triggered manually or scheduled to run periodically.

**Push** is a great way to send any reporting and data insights done inside Whaly to your colleagues, investors or stakeholders (partners, customers, etc.).&#x20;

Recipient of a **Push** doesn't need a direct access to the Whaly platform and it'll meet them where they are (Email, Slack, Google Sheets), hence it'll improve the adoption of any reporting done inside Whaly 🤘

## 🪄 Creating/Listing Push

On Dashboards and Questions, you can click on the "**⚡️ Push**" button at the top right of the screen to list available **Push** and create new ones.

![](<../.gitbook/assets/image (190).png>)

## 🎨 Formats

When data is pushed, Whaly is converting it to a Format. Available formats includes:

* Screenshot
  * PDF
  * PNG
* Raw data
  * CSV
  * JSON

{% hint style="warning" %}
Depending on the Destination and on the report type (Dashboard / Question), some formats won't be available.

Raw data formats are only available for **Questions**.
{% endhint %}

## ➡️ Trigger

Push are currently supporting 2 triggers mode:

* **Manual trigger**: You can trigger any push directly from the Whaly interface at any time. You can do it by configuring the Recurrence to "On demand".
* **Periodic trigger**: You can setup an Hourly, Daily, Weekly or Monthly recurrence to automate a push so that you don't have to think about it anymore.

### ⏰ Periodic trigger parameters

#### Hourly

In this mode, the push will be done at the start of the hour, every hour.

#### Daily

![](<../.gitbook/assets/image (227).png>)

You can select the Day on which the Push will be done:

* **Every day**
* **Business day**: This will execute the push from Monday to Friday

You can also set the hour of the day on which you want the push to execute. The timezone of your computer will be used.

#### Weekly

![](<../.gitbook/assets/image (193).png>)

You can select the Day of the week on which the push should execute. Also, the hour at which it'll be done.

#### Monthly

![](<../.gitbook/assets/image (169).png>)

You can select the day of the Month on which the Push should be done:

* **First day of the Month**
* **Last day of the Month**
* **Nth day of the Month**: You can set the day of the month on which the push should execute (ex. 7th day of the Month)

## 📍Destination

A push is sending data to a Destination. Available destinations are:

* Email (no configuration needed)
* [All previously installed action](actions/)

After selecting the Destination, you'll be prompted with the configuration form so that you can send the data to the proper place with the right credentials.
