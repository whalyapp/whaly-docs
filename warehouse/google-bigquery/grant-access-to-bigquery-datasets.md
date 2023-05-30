# Grant access to BigQuery datasets

By default, Whaly will only have access to the Datasets created by Whaly connectors. In order to grant access to already existing BigQuery Datasets, you should follow those steps:

1. Go to the BigQuery Admin Console

<figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

2. On the left panel, click on one Dataset name (ex. "Days") to open it
3. On the Dataset page, click on "Sharing > Permissions" menu item

<figure><img src="../../.gitbook/assets/image (2) (1) (1).png" alt=""><figcaption></figcaption></figure>

4. In the side panel that opens, click on "Add Principal"

<figure><img src="../../.gitbook/assets/image (1) (2).png" alt=""><figcaption></figcaption></figure>

5. In the "New principals" search bar, select the Service Account configured in Whaly. And in the "Assign roles", select the "BigQuery Data Viewer" role.

<figure><img src="../../.gitbook/assets/image (4) (2).png" alt=""><figcaption></figcaption></figure>

6. Click on "Save"

<figure><img src="../../.gitbook/assets/image (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

And that's it! Whaly will now let users import tables from this BigQuery Dataset 🎉
