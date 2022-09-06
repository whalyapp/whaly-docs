# Facebook Ads

## **Why syncing my Facebook Ads to** [**Whaly**](https://whaly.io)**?**

Syncing your Facebook Ads can be useful for various cases:

* Consolidate your Facebook Ads performance with your others marketing channels (Google, LinkedIn etc.)
* Include Facebook Ads into your Customer Acquisition Cost definition
* Compare your marketing spent with your revenue to be sure that your marketing budget is properly sized
* Provide an access on the Facebook Ads performance to stakeholders (colleagues, partners, investors) without giving them access to the Facebook Ads console
* ...

## Which Facebook Ads data is synced by [Whaly](https://whaly.io)?

[Whaly](https://whaly.io) 🐳 is currently syncing the following data:

### Reports

* **Ad Account:** An ad account is used for managing ads of Facebook. Each ad account can be managed by multiple users, and users can have one or more different levels of access to an account, configured by specifying roles for each user.
* **Basic All Level**: See the spent and performance of your Facebook campaigns at the Campaign/Adset/Ad level.

[You can find the relationship between all those objects here.](https://docs.google.com/presentation/d/1Xtx5hmGpmDtWkyFnFtuQsV-sC4ifdYEGb19z4DlKcbg/edit?usp=sharing)

{% embed url="https://docs.google.com/presentation/d/1Xtx5hmGpmDtWkyFnFtuQsV-sC4ifdYEGb19z4DlKcbg/edit?usp=sharing" %}

## Resolving a token expiration issue

By default, Facebook Ads only provides access to your account for 60 days. After this time, your syncs will fails. You'll have 2 ways of unblocking the sync:

a. Create a new access token and use it on your Facebook Ads source. This will have to happen every 60 days. [See more info here](facebook-ads.md#undefined)

b. Create a long lived access token on Facebook and use it. [See more info here](facebook-ads.md#granting-long-term-access-to-whaly)

## Refreshing an Access Token

In order to refresh an access token that has become invalid, you can follow these steps:

a. Create a new Facebook Ads integration from Whaly catalog

b. In the "Configuration" panel of the newly created source, copy the Access Token that was generated

c. In the "Configuration" panel of the source in error, replace the old token with the new Access Token

d. Force a sync on the source

e. You can delete the Facebook Ads source that you created to generate a new token

{% hint style="warning" %}
Be sure to delete the "new" Facebook Ads and not the historical integration, otherwise you'll break your existing reporting.

If you did it by error, [contact Whaly support](../../../guides/support.md#how-do-i-contact-the-support-team) to get assistance!
{% endhint %}

## Granting Long term access to Whaly

By default, when using your Facebook account, you can only give access to your Facebook Ads reporting for 60 days.

After those 60 days, Whaly will be disconnected from your Facebook account for security reasons. The below guide will enable you to give long term access to Whaly to your Facebook account.

This procedure takes 10min so be sure to plan the time ahead! ⏱

It'll be done in 3 parts:

1. Create a Facebook App
2. Create a System User and generate an Access Token from it
3. Enter the Access Token within Whaly 🐳

{% hint style="warning" %}
This guide need you to already have setup a Facebook Business Manager account under which you manage your Ad Accounts to run your campaigns.

If you don't already have a Facebook Business Manager account, please create one before following this guide. [You can find instructions here.](https://www.facebook.com/business/help/1710077379203657)
{% endhint %}

### 1 - Create a Facebook App

1. Go to the App Creation workflow by clicking [on this link](https://developers.facebook.com/apps/create/). Then select "**Manage integration for your business**"

![](<../../../.gitbook/assets/image (147).png>)

2\. Select the "**Business**" app type

![](<../../../.gitbook/assets/image (148).png>)

3\. Give a name to your App such as "**Whaly Sync**" and make sure to **attach it to your Business Manager Account**

![](<../../../.gitbook/assets/image (150).png>)

4\. You're all set 🎉

### 2 - Create a System User

1. Connect to your **Facebook Business Settings** by clicking [on this link](https://business.facebook.com/settings/system-users)
2. Click on "**Add**" to create a System User

![](<../../../.gitbook/assets/image (143).png>)

3\. Name it "**Whaly**" and give it an **Employee** user role

![](<../../../.gitbook/assets/image (144).png>)

4\. Click on "**Add Assets**"

![](<../../../.gitbook/assets/image (145).png>)

5\. Add the **Ad Account** that you want to sync within Whaly and give it the "**View performance**" access

![](<../../../.gitbook/assets/image (146).png>)

6\. Click on "**Generate Token**"

![](<../../../.gitbook/assets/image (155).png>)

7\. Select the App you created in the previous chapter. Also, makes sure to add the "**ads\_read**" permission and then **Save**.

![](<../../../.gitbook/assets/image (151).png>)

![](<../../../.gitbook/assets/image (152).png>)

8\. Copy paste the **Access Token**

![](<../../../.gitbook/assets/Screenshot 2021-09-21 at 15.07.39.png>)

### 3 - Setup the Access Token in your Whaly Account

1. Open the Sources navigation screen by clicking the 🔌 icon on the left navigation bar.
2. Click on **Facebook Ads** source

![](<../../../.gitbook/assets/image (153).png>)

3\. Click on "**Settings**" tab and then on "**Access Token**"

![](<../../../.gitbook/assets/image (154).png>)

4\. In the text input, paste your token created in the previous step

5\. You're all set 🎉
