# Connect your BigQuery

In order to connect your BigQuery instance, Whaly needs to be connected with your Google Cloud Instance. This guide will details the necessary steps:

1. Finding your Google Cloud Project ID
2. Creation of a Google Cloud Service Account with the proper role

{% hint style="info" %}
Steps where you need to paste info from the google cloud console to Whaly are identified with a :scissors:
{% endhint %}

### Prerequisites <a href="#prerequisites" id="prerequisites"></a>

To connect BigQuery to Whaly, you need the following:

* A Google Cloud Project
* Admin rights on the Google Cloud Console

## 1. Find your project ID

You need to grant Whaly access to your BigQuery cluster so we can create and manage tables for your data, and periodically load data into those tables.

* Go to your Google Cloud Console's [projects list](https://console.cloud.google.com/cloud-resource-manager?pli=1).
* :scissors: Find your **Project ID** and paste it into Whaly.

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

:scissors: Then, [create a Private key (JSON) for your service account](https://cloud.google.com/iam/docs/creating-managing-service-account-keys). Open it with your favourite text editor and paste the whole file content into Whaly.
