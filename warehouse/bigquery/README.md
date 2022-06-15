# 🔷 BigQuery

In order to connect your BigQuery instance, Whaly needs to be connected with your Google Cloud Instance. This guide will details the necessary steps:

1. Creation of a Google Cloud Service Account, that will be used for Whaly to get access to your BigQuery
2. Creation of a Google Cloud Storage bucket that will be used for Whaly to load data into your BigQuery
3. Setup of the necessary credentials into Whaly interface

### Prerequisites <a href="#prerequisites" id="prerequisites"></a>

To connect BigQuery to Whaly, you need the following:

* A Google Cloud Project

## 1. Create a Google Cloud Service Account

In order to give access to part of your Google Cloud account, you have to create what is called a "Service Account".&#x20;

A Service Account represent in Google Cloud is a technical user that will have some permissions and credentials to access your cloud ressources.

#### A. Find Project ID <a href="#findprojectid" id="findprojectid"></a>

You need to grant Whaly access to your BigQuery cluster so we can create and manage tables for your data, and periodically load data into those tables.

1. Go to your Google Cloud Console's [projects list](https://console.cloud.google.com/cloud-resource-manager?pli=1).
2. Find your **Project ID** and make a note of it. You will need it to configure Whaly.

![](<../../.gitbook/assets/image (224).png>)

**B. Create service account**

**In order to create the service account that will be used by Whaly to connect to your BigQuery,** see [Google's Creating a service account documentation](https://cloud.google.com/iam/docs/creating-managing-service-accounts#creating).

[Create a Private key (JSON) for your service account. Make a note of it. You will need it to configure Whaly.](https://cloud.google.com/iam/docs/creating-managing-service-account-keys)

**C. Configure service account**

1. Go back to the **IAM & admin** tab, and go to the [project members list](https://console.cloud.google.com/iam-admin/iam/project).
2. Select **+ Add**.

![](<../../.gitbook/assets/image (225).png>)

**D.** In the **New Members** field, enter the service account you created in Step 2. The service account is the entire email address.

E. Click **Select a role > BigQuery > BigQuery Admin**.

![](<../../.gitbook/assets/Screenshot 2021-11-02 at 14.42.48.png>)

## 2. Creation of a Google Cloud Storage bucket

In Google Cloud, Cloud Storage buckets are data repositories that are used to load or save data within Google Cloud.

Whaly is using a Google Cloud Storage bucket to load data from its connector into your BigQuery tables.

A. Go to the **Cloud Storage** tab, and go to the [browser page](https://console.cloud.google.com/storage/browser).

B. Click on "Create Bucket"

![](<../../.gitbook/assets/image (221).png>)

C. Configure the bucket:

Name: The name that you want to keep, ex. "whaly-connectors-loading-deck"

Location type: We advise "Multi-region" for maximum reliability

Location: The region in which your BigQuery data is (EU / US)

Storage class: Standard

Access control: Fine grained

Protection tool: None

D. **Assign permissions to service account**

You must give the service account (in the setup form) **Storage Admin** permission for the bucket, so that it can read and write the data from the bucket.

1. In your Google Cloud Console, go [**Storage > Browser**](https://console.cloud.google.com/storage/browser?\_ga=2.91914202.-115928388.1548358412) to see the list of buckets in your current project.
2. Select the bucket you want to use.

![](<../../.gitbook/assets/image (189).png>)

3\. Go to **Permissions** and then click **Add Members**.\


![](<../../.gitbook/assets/image (166).png>)

4\. In the **Add members** window, enter the Whaly service account you created in Step 3.

5\. From the **Select a role** dropdown, select **Storage Admin**.\


![](<../../.gitbook/assets/Screenshot 2021-12-21 at 13.55.06.png>)
