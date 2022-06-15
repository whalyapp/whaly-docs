# 1⃣ Using the exploration page and creating a chart

**Objectives:** in this first exercise we will learn on to duplicate a tile, how the exploration page work and how to create basic chart.&#x20;

### Duplicating a tile

In the first step we will duplicate our "Order per week" tile. To do so:

1. Open the Training report
2. In edit mode, click on duplicate tile.
3. On the new tile, open the submenu and click on "Edit tile"

![](<../.gitbook/assets/duplicate tile.gif>)

### Using the exploration page

We are now on the exploration page. You can think of this page as the dynamic chart screen in excel. This page is structured with three panels:

1. On the left, we have all our exploration content. It contains our data tables, as well as our metrics (in blue), and our dimensions (in green). We also have related data, based on the tables relationships that we have seen in the previous article.
2. On the middle, we have our query visualiser. This is where we will set the measures we want to see, the filters we want to apply as well as the dimensions we want to break our metrics with. We can also change the cart type that we generate here.
3. On the right, we have our charts options, allowing use to customise the look of our chart.

### Creating our number of order by status chart

The exercise wants to create the following chart :&#x20;

> Add Order breakdown per Order status

To do it based on our initial chart, this is quite simple:&#x20;

1. Group your visualisation using the "Status" dimension
2. Click on run query
3. To stack the bars, pivot the graph on Status.&#x20;
4. Click on update tile

![](<../.gitbook/assets/group by status.gif>)

That's it :tada: Our chart now represents the number of order grouped by week and by order status. Let's move on the next exercise to learn more about metrics and calculated metrics.
