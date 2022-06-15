# 👬 Create a partner dashboard

**Objective**

In every partnership, it is important to share, be it in life, in love or in business. For example, if your company outsources part of its lead acquisition process to external partners, it is important for them to have an overview of how successful you are with converting their leads into deals.

In this guide, you will learn how to structure and configure a partner dashboard that enables you to securely share this information back with your partners.&#x20;

### High level plan

* Understanding our partner dashboard
* Making our dashboard partner-ready
  * Adding a partner filter to our dashboard
  * Adding a sharing link
  * Hiding the partner filter from the report

### Understanding our partner dashboard

For this guide, we will assume that we have already built our Partner Dashboard, which gives us information about:

* Our leads conversion funnel
  * Number of new leads received
  * Number of qualified leads
  * Number of converted leads
* Our partners based generated revenue&#x20;
* Our partners commission&#x20;

You can take a look at our example dashboard below:&#x20;

![](<../.gitbook/assets/image (192).png>)

### Making our dashboard partner ready

#### Adding a partner filter to our dashboard

To make our dashboard partner ready, we will firstly need to be able to breakdown our view per partner. This steps essentially consists in adding a "Partner" filter to our dashboard, and will allow us to restrict the leads to the partner they are generated from.&#x20;

Let's get to work. On Whaly, open your partner dashboard, then:&#x20;

* click on Edit
* click on Add a filter
* select you partner identifier in the "Fields to filter from" list (in this example we will use `partner_name`) and give your filter a name
* in the "Tiles to update" tab, verify that the filter is applied to all the tiles you need

![](<../.gitbook/assets/add filter (1).gif>)

### Adding a sharing link&#x20;

We will use the sharing link feature to create a pre-filtered view of our dashboard that we will be able to send to our partners.

In order to do so:&#x20;

* Click on share
* Click on new sharing link
* Give it a name (we will use "Partner: Duff"), a password if you need to, and select set partner filter value to your partner's name.&#x20;

![](<../.gitbook/assets/sharing link.gif>)

### Hiding the partner filter from the report

Great, now we have a sharing link. But before sending it, we will probably want to prevent our partner to filter on our others partners. To do so, we will hide the partner filter from the dashboard:&#x20;

* Click on edit
* Click on the partner filter settings
* Check "Hide your filter from the report" and save

![](<../.gitbook/assets/hide filter.gif>)

That's it, now we can send our sharing links to our partners. They will be able to view the dashboard to gain insights of how the partnership is performing :tada:

