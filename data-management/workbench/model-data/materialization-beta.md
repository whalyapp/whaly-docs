# 📥 Persistence Engine

When you start to heavily using models you might experience the overall loading time of reports increasing. That's because your warehouse is doing too much at query time. You might also react the limits of your warehouse and some queries might not work anymore.

Or you might want to reuse a Whaly model in an alternative tool such as another visualisation tool or in a reverse ETL.

In order to remediate to both those issues you can materialise your models as view or as tables by using Whaly Persistence Engine.

Whaly Persistence Engine will compute the lineage of your Models and depending on the materialisation configuration done for each model, it will write down its results in your Warehouse.

Future queries done by dashboards and charts will be done on top of those materialisation results.

Persistence Engine can materialise each model in 3 ways:

* No materialisation: This is keeping the Model "virtual" and means that it won't be written to your Warehouse.
* Materialise as a View: This will persist only the SQL query of the models in your Warehouse but each future read will still execute the SQL query. This won't save you compute costs but it will expose the Models in your Warehouse and each query will always returns the most up to date results.
* Materialise as a Table: This will persist the results of the SQL query in your Warehouse. This means that future reads won't execute the Model SQL again but only read the previous result. This is a cost saver but Data Consumer won't have access to the most up to date data, only the one of the last materialisation job run.

