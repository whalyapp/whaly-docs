# 🧹 Configure a Cloud Storage cleaning rule

In order to keep the amount of data stored in the bucket that you created for the connectors, you can follow the following steps to create a Cleaning Rule that will automatically delete any files in the Bucket after 15 days.

1. In the Bucket configuration, open the "LIFECYCLE" panel and then, click on ADD A RULE"

![](<../../.gitbook/assets/Screenshot 2022-05-18 at 11.01.57.png>)

2\. In the "Select an action" list, select "Delete object"

![](<../../.gitbook/assets/Screenshot 2022-05-18 at 11.02.11 (1).png>)

3\. In the "Select object conditions", select the "Age" parameter and set "15 days" and click on "CONTINUE"

![](<../../.gitbook/assets/Screenshot 2022-05-18 at 11.02.33.png>)

4\. Click on "CREATE"

![](<../../.gitbook/assets/Screenshot 2022-05-18 at 11.02.51.png>)

And you are all set 🤗
