# Connect your BigQuery

In order to connect your BigQuery instance, Whaly needs to be connected with your Google Cloud Instance. This guide will details the necessary steps:

1. Finding your Google Cloud Project ID
2. Creation of a Google Cloud Service Account
3. Creation of a Google Cloud Storage Bucket
4. Giving permissions to your service account to access BigQuery and the Storage Bucket

{% hint style="info" %}
Steps where you need to paste info from the google cloud console to Whaly are identified with a :scissors:
{% endhint %}

### Prerequisites <a href="#prerequisites" id="prerequisites"></a>

To connect BigQuery to Whaly, you need the following:

* A Google Cloud Project
* Billing enabled on your Google Cloud Project
* Admin rights on the Google Cloud Console

## 1. Find your project ID

You need to grant Whaly access to your BigQuery cluster so we can create and manage tables for your data, and periodically load data into those tables.

* Go to your Google Cloud Console's [projects list](https://console.cloud.google.com/cloud-resource-manager?pli=1).
* :scissors:Find your **Project ID** and paste it into Whaly.

![](<../../.gitbook/assets/image (228).png>)

## 2. Create a Google Cloud service account

In order to give Whaly access to a subset of your Google Cloud account, you have to create a Service Account. In Google Cloud, a service account is a technical user that will have some permissions and credentials to access your cloud ressources.

**A. Create the service account**

In order to create the service account that will be used by Whaly to connect to your BigQuery, see [Google's Creating a service account documentation](https://cloud.google.com/iam/docs/creating-managing-service-accounts#creating).

**B. Make the service account a BigQuery admin**

* Go back to the **IAM & admin** tab, and go to the [project members list](https://console.cloud.google.com/iam-admin/iam/project).
* Select **+ Add**.

![](<../../.gitbook/assets/image (229).png>)

* In the **New Members** field, enter the service account you created in Step 2.A. The service account is the entire email address.
* Click **Select a role > BigQuery > BigQuery User**.

<figure><img src="../../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

**C. Download the service account private key**

:scissors:Then, [create a Private key (JSON) for your service account](https://cloud.google.com/iam/docs/creating-managing-service-account-keys). Open it with your favourite text editor and paste the whole file content into Whaly.&#x20;

## 3. Create a Google Cloud Storage bucket

In Google Cloud, Cloud Storage buckets are data repositories that are used to load or save data within Google Cloud. Whaly is using a Google Cloud Storage bucket to load data from its connector into your BigQuery tables.

* Go to the **Cloud Storage** tab, and go to the [browser page](https://console.cloud.google.com/storage/browser).
* Click on "Create Bucket"

![](<../../.gitbook/assets/image (224).png>)

* Create the bucket:
  * Name: The name that you want to keep, ex. "`whaly-connectors-loading-deck`"
  * Location type: We advise "Multi-region" for maximum reliability
  * Location: The region in which your BigQuery data is (EU / US) --> :scissors:Set the same value in the Whaly form.&#x20;
  * Storage class: Standard
  * Access control: Fine grained
  * Protection tool: None
* :scissors:Open the details for the bucket you've just created, open the configuration tab, and paste the gsutil URI into Whaly :&#x20;

![](<../../.gitbook/assets/image (176).png>)

## 4. Give permissions to the service account

You must give the service account (in the setup form) **Storage Admin** permission for the bucket, so that it can read and write the data from the bucket.

* In your Google Cloud Console, go [**Storage > Browser**](https://console.cloud.google.com/storage/browser?\_ga=2.91914202.-115928388.1548358412) to see the list of buckets in your current project.
* Select the bucket you want to use.

![](<../../.gitbook/assets/image (191).png>)

* Go to **Permissions** and then click **Add Members**.

![](<../../.gitbook/assets/image (166).png>)

* In the **Add members** window, enter the Whaly service account you created in Step 3.
* From the **Select a role** dropdown, select **Storage Admin**

![](<../../.gitbook/assets/Screenshot 2021-12-21 at 13.55.06.png>)

That's it, your cloud console is all set for Whaly :tada:
