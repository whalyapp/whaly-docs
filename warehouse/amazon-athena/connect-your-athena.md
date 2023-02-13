# Connect your Athena

In order to connect your Athena cluster, Whaly needs some credentials. This guide will details the necessary steps:

1. Create an IAM User and generate an Access Key (+secret)
2. Select your region & work group

### Prerequisites <a href="#prerequisites" id="prerequisites"></a>

To connect Athena to Whaly, you need the following:

* An AWS Project
* Admin rights on the AWS Project (to create IAM User, custom policy and a S3 Bucket)
* An S3 bucket on which the query results can be written. [You can create one if needed.](https://docs.aws.amazon.com/AmazonS3/latest/userguide/create-bucket-overview.html)&#x20;

{% hint style="info" %}
To save cost on the Output Bucket, you can configure [its Bucket Lifecycle rule](https://docs.aws.amazon.com/AmazonS3/latest/userguide/object-lifecycle-mgmt.html) to delete any file after 1 day as the results won't be used after a query have resolved.&#x20;
{% endhint %}

## Create an IAM User and generate an Access Key (+secret)

To connect to your AWS Athena cluster, Whaly need to have a User and its credentials (Access Key). In order to create such a User, [please follow this guide.](https://docs.aws.amazon.com/IAM/latest/UserGuide/id\_users\_create.html)

When being asked which permissions and policies the user should have, [please create a custom Policy](https://docs.aws.amazon.com/IAM/latest/UserGuide/access\_policies\_create.html) that have the following rights:

{% hint style="info" %}
In the Policy definition, you need to fill the ARNs of the S3 buckets that Whaly will have access to.&#x20;

Whaly user needs to access to 2 kinds of S3 buckets:

* Input buckets: Those are the buckets in which you have the data that is being queried by Athena
* A single Output bucket: This is the bucket that Whaly will use to store the query results
{% endhint %}

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "athena:GetTableMetadata",
                "athena:StartQueryExecution",
                "athena:ListDataCatalogs",
                "athena:GetQueryResults",
                "athena:GetDatabase",
                "athena:GetDataCatalog",
                "athena:ListWorkGroups",
                "athena:ListQueryExecutions",
                "athena:GetWorkGroup",
                "athena:StopQueryExecution",
                "athena:ListEngineVersions",
                "athena:GetQueryResultsStream",
                "athena:ListDatabases",
                "athena:GetQueryExecution",
                "athena:ListTableMetadata",
                "athena:BatchGetQueryExecution"
            ],
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "glue:GetDatabases",
                "glue:GetDatabase",
                "glue:GetTables",
                "glue:GetTable",
                "glue:GetPartition",
                "glue:GetPartitions",
                "glue:BatchGetPartition"
            ],
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "s3:PutObject",
                "s3:GetObject",
                "s3:ListBucketMultipartUploads",
                "s3:PutBucketPublicAccessBlock",
                "s3:AbortMultipartUpload",
                "s3:CreateBucket",
                "s3:ListBucket",
                "s3:GetBucketLocation",
                "s3:ListMultipartUploadParts"
            ],
            "Resource": [
            // In this list, you should include the S3 ARNs of both inputs and output buckets
            // Ex:
            // Output bucket
            // "arn:aws:s3:::whaly-athena-output/*",
            // "arn:aws:s3:::whaly-athena-output",
            // Input buckets
            // "arn:aws:s3:::whaly-athena-input",
            // "arn:aws:s3:::whaly-athena-input/*",
            // ...
            ]
        }
    ]
}
```

* Once the IAM User created with the proper policy, [you can create an Access Key](https://docs.aws.amazon.com/IAM/latest/UserGuide/id\_credentials\_access-keys.html) under it to retrieve the **Access Key Id** and the **Access Key Secret**.

## Select your region & Workgroup

In order to properly query your Athena data, Whaly needs to know in which region you want to run the compute. It should be one of the [AWS Region](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Concepts.RegionsAndAvailabilityZones.html) (ex. us-east1). A good practise would be to use the same one as the one you are using when doing SQL Queries in the console:

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

Also, you'll need to [select an existing work group or create one.](https://docs.aws.amazon.com/athena/latest/ug/workgroups-create-update-delete.html) Inside Whaly, you'll need to pass the name of the Workgroup you wish to use when querying your data with Whaly.
