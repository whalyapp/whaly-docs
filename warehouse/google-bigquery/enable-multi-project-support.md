# Enable multi project support

It is possible to query datasets stored in other Google Cloud Project than in the "primary" project that is configured. BigQuery compute cost will still be charged in the "primary" project, but it gives you more flexibility to organize your Warehouse to use multiple projects.

To activate multi project support, you need to do the following in Google Cloud console:

a. Activate the [Cloud Resource Manager API](https://console.developers.google.com/apis/api/cloudresourcemanager.googleapis.com/overview) **on the primary project ID** configured in Whaly

b. Give IAM permissions (Role: **`BigQuery User` ** or ** `BigQuery Admin`**) to the Whaly Service Account in each of the projects you want to add

c. (only if granted role is **`BigQuery User`** in previous step) For each datasets to the Datasets stored in secondary projects [grant access to Whaly](grant-access-to-bigquery-datasets.md).
