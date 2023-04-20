# Stripe

## **Why syncing my Stripe to** [**Whaly**](https://whaly.io)**?**

Syncing your Stripe can be useful for various cases:

* Consolidate your customer database (Postgres, CRM) and the status of your customer payments
* Track and share your company revenue internally
* ...

## Which Stripe data is synced by [Whaly](https://whaly.io)?

[Whaly](https://whaly.io) 🐳 is currently syncing the following data:

### Core

* **Balance Transaction**: Balance transactions represent funds moving through your Stripe account.
* **Charge**: To charge a credit or a debit card, you create a Charge object.
* **Customer**: Customer objects allow you to perform recurring charges, and to track multiple charges, that are associated with the same customer.
* **Dispute:** A dispute occurs when a customer questions your charge with their card issuer.
* **Fee**: Fees (in cents) paid for a Balance Transaction.
* **Payment Intent**: A PaymentIntent guides you through the process of collecting a payment from your customer.
* **Payout**: A Payout object is created when you receive funds from Stripe, or when you initiate a payout to either a bank account or debit card of a [connected Stripe account](https://stripe.com/docs/connect/bank-debit-card-payouts).

### Product

* **Product**: Products describe the specific goods or services you offer to your customers.
* **Coupon**: A coupon contains information about a percent-off or amount-off discount you might want to apply to a customer or to a subscription.
* **Subscription Discount**: A subscription discount represents the actual application of a coupon to a particular Subscription.

### Billing

* **Invoice**: Invoices are statements of amounts owed by a customer, and are either generated one-off, or generated periodically from a subscription.
* **Invoice Line Item**: The individual line items that make up an invoice.
* **Invoice Item**: Invoice Item are used when you want to add a charge or credit to a customer, but actually charge or credit the customer's card only at the end of a regular billing cycle.
* **Plan**: Plans define the base price, currency, and billing cycle for recurring purchases of products.
* **Subscription**: Subscriptions allow you to charge a customer on a recurring basis.

### Connect

* **Account**: This is an object representing a Stripe account.
* **Transfer**: A Transfer object is created when you move funds between Stripe accounts as part of Connect.

## Metadata support

Many Stripe objects support metadata, which contains custom fields in which you can write custom values (User Id, etc.) to help reconcile the data with your database and other referentials.

Whaly automatically detect all the metadata fields and create a new column for each in the destination table. Those columns names are prefixed with `metadata_`.

## Schema

{% embed url="https://docs.google.com/presentation/d/1Ux_gO5LjObJ1cP_M7_w2tit2oDk2Uu7iwzBCz9mxt8o/edit" %}

[You can find the relationship between all those objects here.](https://docs.google.com/presentation/d/1Ux\_gO5LjObJ1cP\_M7\_w2tit2oDk2Uu7iwzBCz9mxt8o/edit?usp=sharing)
