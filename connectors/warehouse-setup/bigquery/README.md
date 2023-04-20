# BigQuery

In order to write Data into your BigQuery warehouse, Whaly needs additional configuration on Google Cloud side. This guide will details the necessary steps:

1. Creation of a Google Cloud Storage Bucket
2. Giving permissions to your service account to the Storage Bucket

{% hint style="info" %}
Steps where you need to paste info from the google cloud console to Whaly are identified with a :scissors:
{% endhint %}

### Prerequisites <a href="#prerequisites" id="prerequisites"></a>

To connect BigQuery to Whaly, you need the following:

* A Google Cloud Project
* Billing enabled on your Google Cloud Project
* Admin rights on the Google Cloud Console
* A Service Account already configured in Whaly

## 1. Create a Google Cloud Storage bucket

In Google Cloud, Cloud Storage buckets are data repositories that are used to load or save data within Google Cloud. Whaly is using a Google Cloud Storage bucket to load data from its connector into your BigQuery tables.

* Go to the **Cloud Storage** tab, and go to the [browser page](https://console.cloud.google.com/storage/browser).
* Click on "Create Bucket"

![](<../../../.gitbook/assets/image (224).png>)

* Create the bucket:
  * **Name**: The name that you want to keep, ex. "`whaly-connectors-loading-deck`"
  * **Location** type: We advise "Multi-region" for maximum reliability
  * **Location**: The region in which your BigQuery data is (EU / US) --> :scissors:Set the same value in the Whaly form.
  * **Storage class**: Standard
  * **Access control**: Fine grained
  * **Protection tool**: None
* :scissors:Open the details for the bucket you've just created, open the configuration tab, and paste the gsutil URI into Whaly:

![](<../../../.gitbook/assets/image (176).png>)

## 2. Give permissions to the Whaly Service Account on the Cloud Storage Bucket

You must give the service account (in the setup form) **Storage Admin** permission for the bucket, so that it can read and write the data from the bucket.

* In your Google Cloud Console, go [**Storage > Browser**](https://console.cloud.google.com/storage/browser?\_ga=2.91914202.-115928388.1548358412) to see the list of buckets in your current project.
* Select the bucket you want to use.

![](<../../../.gitbook/assets/image (191).png>)

* Go to **Permissions** and then click **Add Members**.

![](<../../../.gitbook/assets/image (166).png>)

* In the **Add members** window, enter the **Whaly service account email**.
* From the **Select a role** dropdown, select **Storage Admin**

![](<../../../.gitbook/assets/Screenshot 2021-12-21 at 13.55.06.png>)

3. In Whaly, go in your "Warehouse" page in the Settings and paste the `gsutil URI` value in the "GCS Bucket Name" field.

<figure><img src="../../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

That's it, your BigQuery setup is all set for being used with Whaly connectors :tada:
