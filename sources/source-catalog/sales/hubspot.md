# Hubspot

## **Why syncing my Hubspot to** [**Whaly**](https://whaly.io)**?**

Syncing your Hubspot can be useful for various cases

* Understand who your contacts are
* Analyse your deal pipeline variation on a weekly / monthly basis
* Check the effect of your marketing campaigns on sales
* Build Sales Rep performance dashboards to animate your sales team
* Reconcile your Sales closed amount with the cash that you really collected
* ...

## Which Hubspot data is synced by [Whaly](https://whaly.io)?

[Whaly](https://whaly.io) 🐳 is currently syncing the following data:

### Sales

* **Contact**: Anyone who interacts with your business.
* **Company**: Organizations that you interact with.
* **Deal**: Tracks potential revenue.
* **Deal Pipeline**: Represent your sales process(es).
* **Deal Pipeline Stage**: Steps in your pipeline that signify to your sales team that an opportunity is moving toward the point of closing.
* **Deal Stage History**: Tracks the history of Deal Stage changes, for each Deal.
* **Deal x Contact Association**: Associate Deals with their related Contacts.
* **Deal x Company Association**: Associate Deals with their related Companies.
* **Engagement**: An engagement is an action (an email, call, meeting, task or note) attached to a Deal, Contact and Company.
* **Engagement x Contact Association**: Link Contacts and associated Engagement.
* **Engagement x Company Association**: Link Companies and associated Engagement.
* **Engagement x Deal Association**: Link Deals and associated Engagement.

### Engagement

* **Call Engagement**: A Call engagement is a phone call attached to a Deal, Contact and Company.
* **Meeting Engagement**: A Meeting engagement is a meeting attached to a Deal, Contact and Company.
* **Task Engagement**: A Task engagement is a Task attached to a Deal, Contact and Company.

### Marketing

* **Form**: Use forms to gather important information about your visitors and contacts.
* **Contact Form Submission**: All the form submissions done by your contacts.

### Service

* **Ticket**: Your customer service requests.
* **Deal x Ticket Association**: Associate Deals with their related Tickets.
* **Contact x Ticket Association**: Associate Contacts with their related Tickets.
* **Ticket x Company Association**: Associate Ticket with their related Companies.

### Analytics

* **Traffic Overview**: Gives an overview on your traffic.
* **Traffic by Source**: Gives the traffic breakdown by Source (organic, email, offline, ...).
* **Custom View Traffic by Source**: For a given analytics view, gives the traffic breakdown by Source.
* **Custom Analytics View**: Analytics views are filters that you can use in the Sources tab and the Pages tab in the traffic analytics tool to split the data up for esier analysis. Analytics views can be customised by your domains, visitor country, and more.

### Admin

* **Owner**: HubSpot users that can own things (contacts, deals, tickets, ...).
* **Property:** Contains all the properties definition for the "deals", "contacts", "companies", "tickets", "products", "line\_items" objects.
* **Property Option:** Contains the different options that a given Property can have.
* **Workflows**: Create a workflow to automate your marketing, sales, and service processes and make your team more efficient.
* **Workflow Action - Set Contact Property**: Set a property value on the enrolled contact.
* **Workflow Action - Add Contact Enum Property**: Add an enum value to a contact property.
* **Workflow Action - Copy Property**: Copy a property value of the enrolled contact to another property in the same record.
* **Workflow Action - Datestamp Property**: Set the current date into a Date property.

### Custom Objects

Whaly detects automatically your [Hubspot custom objects](https://knowledge.hubspot.com/crm-setup/use-custom-objects) and their association with other standards (contact, deal, ...) and custom objects in Hubspot.

The name of the generated table and list of fields depends on how you configured your custom objects schemas.



[You can find the relationship between all those objects here.](https://docs.google.com/presentation/d/136dpFgcBg7L65z9\_NCJC5CemAWATkJwzn5q8U4SnNP8/edit?usp=sharing)

{% embed url="https://docs.google.com/presentation/d/136dpFgcBg7L65z9_NCJC5CemAWATkJwzn5q8U4SnNP8/edit?usp=sharing" %}

{% embed url="https://docs.google.com/presentation/d/1vf1lRF_qGRA1qm-eKIxqP5cahnDqM4czQSA4OsnMVrU/edit?usp=sharing" %}

{% embed url="https://docs.google.com/presentation/d/1uwadP2aKE0vQ_962gFaT1rNABESPjgRYrBCsORNriQs/edit?usp=sharing" %}

{% embed url="https://docs.google.com/presentation/d/1j0jv9PTROKzgtDZ9v8GZbvgta-c8Ca9hx3b5xq384QI/edit?usp=sharing" %}

{% embed url="https://docs.google.com/presentation/d/1HxKf6x38cI5BgSYFGskg6DE6aW_A6KXJWx7i5k3xFFc/edit?usp=sharing" %}

{% embed url="https://docs.google.com/presentation/d/1AdkMYzy3wcecm83jO6-MiEWbrb1QIJZRrXmdXx2t1xA/edit?usp=sharing" %}

{% embed url="https://docs.google.com/presentation/d/1efQjxliZGsuMVJW7gKEQ5ZS_pWUugIZL2r8NZnWcRaA/edit?usp=sharing" %}

## Connecting the Source

Granting Hubspot data access to Whaly is done through an OAuth authentication process. The Super Admin of your Hubspot account must give your user the access to App Marketplace integration:

**Step 1 - Have your Super User giving your user the rights to integrate with App Marketplace (**_**Done by the account Super User) - Note : if you already are a Super User**_ [_**jump to this section**_](https://slite.com/api/public/notes/WiIWr5\_WGr/redirect)

1- Go to Settings

2- Click on User & teams at the bottom left of your window

3- Select the user on which you want to grant App Marketplace rights

4- Click on "More" and "Account"

5- Turn the App Marketplace access to on

6- Click on "Save"

**Step 2 - Add Hubspot as a source (**_**Done by the Whaly end user)**_

In Whaly, your user can now access Hubspot :

1\. Click on your sources catalog on the bottom left menu of your window

![](<../../../.gitbook/assets/image (73).png>)

2\. Select Hubspot + Connect

![](<../../../.gitbook/assets/image (123).png>)

3\. You will have to briefly connect to your Hubspot account and accept authentification

4\. Back to Whaly you need to click on "Continue"

Your data source is now set-up, congrats ![🎉](https://mail.google.com/mail/e/1f389). You can see the initial loading and the data updates in the "Sources" menu on the left hand side

![](<../../../.gitbook/assets/image (74).png>)

## Source considerations

1. Due a limitation of Hubspot API, it's impossible to detect Deals and Contacts that have been **deleted** since the last sync. Hence, the connector is running 1 `FULL TABLE` sync per day to make sure that deleted records in Hubspot are deleted in your Warehouse. The rest of the syncs are done using the `INCREMENTAL` replication method to save processing time.
2. **Merged contacts**: In order to identify Contacts that have been merged with another one, the connector is adding a field called `has_been_merged`.When set to `true`, it means that this contact has been merged with another one. To keep the same number as what you would find in Hubspot, you should exclude them for your reporting.
3. **Merged deals**: Merged Deals are deleted during the daily `FULL TABLE` sync.
4. **Custom Objects**: Because of a current limitation of the Custom Objects API, the connector is not able to run INCREMENTAL syncs at every run.
