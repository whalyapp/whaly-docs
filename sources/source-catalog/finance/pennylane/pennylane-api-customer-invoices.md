# Pennylane API - Customer Invoices

## **Why syncing my Pennylane to** [**Whaly**](https://whaly.io)**?**

Syncing your Pennylane account can be useful for various cases:

* Consolidate your customer database (Postgres, CRM) and the status of your customer payments
* Track and share your company revenue internally
* ...

## How to setup Pennylane integration?

In order to fetch from Pennylane the API Token that Whaly requires to run the connector, on Pennylane, please go to "Parameters" > "Developers" screen and generate your token from there.

[You can find more information here](https://support.pennylane.com/fr/articles/5106267-utiliser-l-api-publique-pennylane#h\_c076fa5a3a)

## Which **Pennylane** data is synced by [Whaly](https://whaly.io)?

[Whaly](https://whaly.io) 🐳 is currently syncing the following data:

### Referential

* **Customer**: Customer objects allow you to generate invoices, and to track multiple invoices, that are associated with the same customer.
* **Invoice**: Invoices are statements of amounts owed by a customer.
* **Invoice Line Item**: An invoice line item is a single entry on an invoice.

[You can find the relationship between all those objects here.](https://docs.google.com/presentation/d/18F4Qk1hQLBwLDdTVK8s13ed5QxZLTuq4v1CH4hENmmc/edit#slide=id.g244d368397\_0\_1)

{% embed url="https://docs.google.com/presentation/d/18F4Qk1hQLBwLDdTVK8s13ed5QxZLTuq4v1CH4hENmmc/edit" %}
