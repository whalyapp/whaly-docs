# 4⃣ Creating an exploration and using rollup columns

**Objectives:** in this exercise we will learn how to create an exploration, and how to create more complex calculated columns using the rollup feature.

### Creating an exploration&#x20;

In this exercise we need to:

> Add the number of customers per number of orders

Until now we were using the Order exploration, that was getting data from the order table.

Here, we want to have a chart representing the number of customer per number of order. Some customers may not have placed an order, and we want to count them. So we will need to start our exploration from the customer table and group our customer per number of order.\


Let's create our exploration :&#x20;

* From Whaly home page, click on the exploration logo in the sidebar (compass icon)
* Click on create an exploration
* Select your customer table

![](<../.gitbook/assets/create exploration.gif>)

We have created our first exploration, well done :tada:

### Using rollup columns

On our new exploration, we need to have the number of orders as a dimension. This number of order is not available in the customer table, so we need to add it.

In order to do this, we will need to create a rollup column.

{% hint style="info" %}
A rollup column works like a lookup, but it will match multiple line in the target dataset. It will allow you to decide how you want to aggregate the matched lines (a count, a sum, an average value, ...)
{% endhint %}

Open the workbench on the customer table, and add a rollup column :&#x20;

* Name your columns order\_count
* Select the order dataset
* Use the count feature
* Select the default view
* Save :floppy\_disk:

![](<../.gitbook/assets/order count.gif>)

Now we have the order count for each of our customer. It will be easy to create the chart we want if we go back to our exploration :&#x20;

* Add the order count as a dimension
* Create a bar chart measuring a number of customer grouped by order count

![](<../.gitbook/assets/image (210).png>)

That's it :tada:&#x20;
