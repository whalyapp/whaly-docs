# Configuration

## Prerequisites

In order to use this integration you need:

* An account on [dbt cloud](https://www.getdbt.com/)
* An api access on [dbt cloud](https://www.getdbt.com/) (please note that only paid plan have an API access)
* A service token on the said account
* A job that outputs a `manifest.json` & `run-results.json`
* A job that outputs `sources.json`&#x20;

### Configure your service token on dbt Cloud

Go to your Account **Settings > Service Token** and create a new service token. Give this Service Token access to your desired project as well as the following roles:

* Read Only

<figure><img src="../../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Once your service token is created, copy the key because you will not be able to access it again and save it for later.
{% endhint %}

### Configure your project to output the proper artifacts

In order to get access to your `manifest.json` , `run_results.json` and `source.json` using the API, you should edit your Project Details and associate it with the 2 Jobs that are producing them.

* Documentation Job: Associate it with a Job that output `manifest.json` & `run_results.json`
* Source Freshness: Associate it with a Job that output `source.json`

{% hint style="info" %}
The mapping between the CLI options and the produced outputs is available in [dbt documentation](https://docs.getdbt.com/reference/artifacts/dbt-artifacts#when-are-artifacts-produced).
{% endhint %}

Please reference the proper jobs at the project level:

<figure><img src="../../../.gitbook/assets/image (1) (3).png" alt=""><figcaption></figcaption></figure>

### Find your Account ID and Project ID&#x20;

Open the job that you have configured at the previous step and extract the Account Id and Project Id from your URL.

The url should look like:

```
https://cloud.getdbt.com/next/deploy/<Account Id>/projects/<Project Id>/jobs
```

## Configure Whaly

Open Whaly and go to the [Settings](../../../workspace/settings.md). On the settings please click on **Storage Admin > Models Sync**. You should see a page like this:

<figure><img src="../../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

Click on **Activate dbt Cloud Sync** for modeling.&#x20;

You will then be prompted to enter your Service Token, your Account Id as well as your Project Id.

Once this is done, go into the Workbench and you'll see the dbt icon on the left bar.

Click on it to display the syncs panel. Click on a previous sync to checks its logs or click on the plus sign at the top of the page to trigger a sync between Whaly and dbt Cloud.

<figure><img src="../../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>
