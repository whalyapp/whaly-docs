# Relationships

Relationship are a way of telling Whaly how your datasets are linked together.&#x20;

It's a great way to:

* Combine data from various source&#x20;
* Create detailed explorations

## How can I configure relationship?

To configure a dataset relationship, go to the **information** tab and then scroll to the relationship block and click on **Add a relationship.**

<figure><img src="../../../.gitbook/assets/Screen Cast 2022-09-08 at 7.33.11 PM.gif" alt=""><figcaption><p>Adding relationships</p></figcaption></figure>

In order to add a relationship you need to provide:

* A dataset which will be related to the current dataset
* A column from the current dataset&#x20;
* A column from the related dataset that will match the one selected above in values and in type (example => String can only match String columns)
* A type of relationship&#x20;
  * Has one&#x20;
  * Has many
  * &#x20;Belongs to

## Understanding Relationship Type

Let's imagine we have the three following tables

**Orders**

```
| order_id | amount   | user_id  |
|----------|----------|----------|
| 1        | 90       | 1        | 
| 2        | 10       | 1        |
| 3        | 50       | 2        |
| 4        | 30       | 1        |
| 5        | 20       | 2        |
```

**Users**

```
| user_id  | name            | address_id  |
|----------|-----------------|-------------|
| 1        | Rick Sanchez    | 1           | 
| 2        | Archer Sterling | 2           |
```

**Address**

```
| address_id  | name                 |
|-------------|----------------------|
| 1           | 6910 Smith Residence |
| 2           | Penthouse NYC        |
```

In this example a User has only one address and has multiple orders therefore when setting up relationships we will do:

**Relationship 1:**

* **from dataset**: User
* **to dataset:** Address
* **Type** has one
* **From Column**: address\_id
* **To column**: : address\_id

**Relationship 2:**

* **from dataset**: User
* **to dataset:** Order
* **Type** has many
* **From Column**: user\_id
* **To column**: : user\_id

Please note that has many is the oposite of belongs to, therefore this relationship would have been legit too.

**Relationship 3:**

* **from dataset**: Order
* **to dataset:** User
* **Type** belongs to
* **From Column**: user\_id
* **To column**: : user\_id
