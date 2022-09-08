# Materialization (beta)

When you start to heavily using models you might experience the overall loading time of reports increasing. That's because your warehouse is doing too much at query time. You might also react the limits of your warehouse and some queries might not work anymore. Other time you might want to reuse a query that has been saved as a model in an alternative tool such as another visualisation tool or a reverse ETL.

In order to remediate to those issues you can materialize your models as view or as tables.

## Materialize as view

The view materialisation will write your model's query as a View in your warehouse making it accessible to any other tools from your stack. This will not improve query performance but can overcome some limitation when the query text becomes too big.

## Materialize as table

The table materialisation will take the result of your model's query and create a new table with the result. This will significantly improve the model query time but as we run the materialisation execution periodically this also means that your data is always stale. This is a tradeoff you need to make between speed and real time.
