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
  * Has many
  * Belongs to
  * Has one

## Understanding Relationship Type

Let's imagine we have the three following tables:

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

In this example a User has multiple orders therefore when setting up relationships we will do:

**Relationship 1:**

* **From dataset**: User
* **To dataset:** Order
* **Type** has many
* **From Column**: user\_id
* **To column**: : user\_id

Please note that **"has many"** is the opposite of **"belongs to"**, therefore this relationship would have been legit too:

**Relationship 2:**

* **From dataset**: Order
* **To dataset:** User
* **Type** belongs to
* **From Column**: user\_id
* **To column**: : user\_id

{% hint style="info" %}
Whenever a relationship is created, the symmetric relationship is automatically created on the other dataset.
{% endhint %}

As we have the same number of rows in both the Users and Address as a User can have a single Address and vice versa, we will create a one to one relationship:

**Relationship 3:**

* **From dataset**: User
* **To dataset:** Address
* **Type:** has one
* **From Column**: address\_id
* **To column**: address\_id

{% hint style="warning" %}
The "has one" relationship is quite rare in real world, it's relevant when you have exactly the same number of rows in the two related datasets.
{% endhint %}
