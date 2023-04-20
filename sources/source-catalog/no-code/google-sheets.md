# Google Sheets

## **Why syncing Google Sheets data to** [**Whaly**](https://whaly.io)**?**

Syncing your **Google Sheets** can be useful for various cases

* Importing "offline" data to Whaly (Salaries, Offline Marketing Spent, ...)
* Importing static data to Whaly such as wages
* Importing data that are not available as a direct connector in Whaly

## Which **Google Sheets** data is synced by [Whaly](https://whaly.io)?

[Whaly](https://whaly.io) 🐳 is currently syncing the following data:

* **Sheets**: We sync all your sheets and we will create a dataset for each sheet
* **Sheet Row Data**: For each sheet, Whaly will sync all of the row data as it has been inserted in the spreadsheet.

{% hint style="warning" %}
The Google Sheet connector is only syncing **native** Google Sheet documents.&#x20;

If your Spreadsheet is in the XLSX format (you see a green tooltip next to the spreadhseet name), you have to save it as a Google Sheet firstly. To do so, go yo **File > Save as Google Sheet.**
{% endhint %}

We consider that the first line is the header of your data. Meaning that if you input data such as&#x20;

![](<../../../.gitbook/assets/image (131).png>)

You'll get 3 columns respectively named **id, test and toto.**

{% hint style="danger" %}
**Whaly connector use the values in the first data row to infer the type of the column.**&#x20;

**If the first row of the data contains an empty cell for a column, Whaly will infer that the column is a STRING.**
{% endhint %}

**An example of a spreadsheet structure that work is here:** [**https://docs.google.com/spreadsheets/d/10H-1y5JPq7nFNGKvV1cdOm8A9QJsuYwmk3-biPmzIrU/edit#gid=1639896517**](https://docs.google.com/spreadsheets/d/10H-1y5JPq7nFNGKvV1cdOm8A9QJsuYwmk3-biPmzIrU/edit#gid=1639896517)

{% embed url="https://docs.google.com/spreadsheets/d/10H-1y5JPq7nFNGKvV1cdOm8A9QJsuYwmk3-biPmzIrU/edit#gid=1639896517" %}
**Gotta catch'em all!**
{% endembed %}

## How to connect?

On the catalog page, click on the Google Sheet card.

![](<../../../.gitbook/assets/image (132).png>)

In the next screen, enter your google sheet url:

![](<../../../.gitbook/assets/image (133).png>)

Your Google Sheets url looks like : https://docs.google.com/spreadsheets/d/\[Spreadsheet ID]/edit#gid=0

## Troobleshooting a Google Sheet source in failure

Google sheets being a spreadsheet, it will allow the use of different types of data (string, number, date, boolean, ...) in a same column. This behaviour goes against the principles of SQL databases that needs typed columns in order to be able to work (meaning you can only have one type of data in a column).

As your spreadsheet evolves, you may purposefuly (or not) change the type of a column. When this happens, the connector will create a new column and add the suffix \_\_\_\[NEW\_TYPE] to your ol
