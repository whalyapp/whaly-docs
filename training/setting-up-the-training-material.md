# 0⃣ Setting up the training material

**Objectives:** in this section, you will be guided on setting everything up in order to start training.

{% hint style="info" %}
This steps are usually done on your behalf by Whaly's team before the first onboarding call. You should just check that everything is set-up properly before heading on to the next article :relaxed:
{% endhint %}

## High level plan

1. Connecting our "Jaffle Shop" source
2. Creating our base exploration
3. Creating our base report
4. Adding our first chart

### 1. Connecting our Jaffle Shop source

The first thing we will need to do is connect our training source. In order to do so, simply head to the source catalog and click on the `Jaffle Shop (Training material)` source. Then, click on the `Connect` button.&#x20;

![](<../.gitbook/assets/connect jaffle shop source.gif>)

The Jaffle Shop source is composed of three data tables:

* Customers
* Orders
* Payments

A customer have between 0 and n orders. An order have a customer, and between 1 and n payments. A payment is linked to an order.&#x20;

![Jaffle Shop database schema](<../.gitbook/assets/image (203).png>)

### 2. Creating our training exploration

In order to create our training exploration, head to the template Catalog and click on the Jaffle Shop (training) template. Then, simply click on connect.

![](<../.gitbook/assets/create exploration from template.gif>)

The following exploration will be automatically created in your workspace :&#x20;

![Jaffle Shop order exploration](<../.gitbook/assets/image (264).png>)

### 3. Creating our base report

In order to create our training report :&#x20;

1. Head to your workspace. Click on "Create a new report", give it a name (Training for example) and click on "Continue"
2. Click on text
3. Add the following text in the tile :&#x20;

> Exercise:
>
> 1. \[New Chart] Add Order breakdown per Order status
> 2. \[New Chart + New Metric] Add the payment amount paid with gift cards per month
> 3. \[New Chart + New Column + New Drill] Add the Customer name in the Order drill down
> 4. \[New Chart + New Exploration] Add the number of customers per number of orders

![](<../.gitbook/assets/create base report.gif>)

### 4. Adding our first chart

The first chart we will add is the number of order per week. To do so:&#x20;

1. On the report, click on Edit
2. Click on **Visualization**
3. Select the "Order" exploration from the list&#x20;
4. Then, reproduce the following query :&#x20;
   1. Click on **Timeseries**
   2. Measure: number of order
   3. Time: order date
   4. Select dates between 2018/01/01 and 2018/04/01
   5. Click on Run query, and display as a bar chart :&#x20;

Our dashboard should look like this now :&#x20;

![](<../.gitbook/assets/image (187).png>)

That's it, we are now ready to work on the training exercices. Head on the the next step in order to deep dive on charts creation :diving\_mask:
