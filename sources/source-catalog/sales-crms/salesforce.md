# Salesforce

## **Why syncing my Salesforce data to** [**Whaly**](https://whaly.io)**?**

Syncing your Salesforce can be useful for various use cases:

* Understand who your leads are
* Analyse sales velocity & performance
* Analyse the variation around your Opportunities&#x20;
* Understand your core metrics such as Annual Contract Value, or even Monthly Recurring Revenue.
* ...

## Which Salesforce data is synced by [Whaly](https://whaly.io)?

[Whaly](https://whaly.io) 🐳 is able by default to sync the following data:

* Account
* AccountContactRole
* Contact
* Opportunity
* OpportunityContactRole
* OpportunityCompetitor
* OpportunityStage
* Partner
* PartnerRole
* Lead
* LeadStatus
* CampaignMember
* Campaign
* Order
* User
* Contract

**Add custom objects**

{% hint style="info" %}
In order to save API calls done to your Salesforce instance, the Salesforce connector will ask you to fill an "Allowlist" with the name of the objects that you wish to sync.

Objects that are not in this list won't be read at all by the connector.
{% endhint %}

In order to sync custom objects, you should get their API Name from Salesforce interface and add it to the 'Allowlist of Salesforce Objects to read' connector property in the source settings:

<figure><img src="../../../.gitbook/assets/image (1) (1) (2) (1).png" alt=""><figcaption></figcaption></figure>

Then, the Custom Objects will be shown in the "Selective Sync" screen and you'll be able to sync them / don't sync them from there.

{% hint style="success" %}
In order to help you find the proper "Object API Name", the connector is writing them all at the beginning of any syncs in its logs, make sure to check them!
{% endhint %}

## **Connect your Salesforce instance**

{% hint style="info" %}
**Make sure that your user account has rights for all the aforementioned objects**
{% endhint %}

Start by clicking on the salesforce icon. You should be redirected to the salesforce login page.

![Salesforce login page](<../../../.gitbook/assets/image (211).png>)

Make sure that you login with the proper credentials. One best practice is to create a user dedicated for the salesforce sync, so that you can remove access to this user whenever is needed.

After logging in, you will be redirected to Whaly and the data will start syncing.



