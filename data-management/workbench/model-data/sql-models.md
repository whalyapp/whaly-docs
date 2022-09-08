# SQL Models

SQL Models help you transform data using your warehouse SQL implementation on Whaly interface.

It's a great way to:

* Go beyond Flows capabilities&#x20;
* Use a language you are already familiar with (whaly works with your warehouse SQL so no need to learn a new one)
* Start creating SQL queries that you can compose

## Creating a SQL Model

In order to create a SQL Model, open your **View Selector** on **Data**, click on the **+ button** next to models and select **SQL model**. You can also click on **New** > **Model** > **SQL Model.**

<figure><img src="../../../.gitbook/assets/Screen Cast 2022-09-08 at 6.49.23 PM.gif" alt=""><figcaption><p>Create a SQL Model</p></figcaption></figure>

## Updating a SQL Model

You can modify your SQL model query whenever you need to. In order to do click on the configuration tab, modify the query, run the query (you can save a query only if it outputs data). Before saving data we ask you to provide us the Primary Keys of your model so we know how to use it in an exploration.

<figure><img src="../../../.gitbook/assets/image (6).png" alt=""><figcaption><p>Save a query</p></figcaption></figure>

## Use Composition in your SQL queries

It is very useful to break complicated models into smaller ones that can be more easily managed and more easily debugged. In order to do so Whaly offers you the capability to compose your SQL Queries. It means that you can reference any Sources or Models in your current query and the Whaly query engine will automatically to the interpolation for you.

In order to reference another query, start typing the name of your model or the name of your raw dataset and then hit enter. It should be highlighted in your query in blue. You can click on the dataset reference to open it in a new tab if you wish to introspect it.&#x20;

<figure><img src="../../../.gitbook/assets/Screen Cast 2022-09-08 at 6.58.09 PM.gif" alt=""><figcaption></figcaption></figure>
