# Filter

## What does it do?

It allows you to filter rows from your model.

## How to use it?

On any previously steps available in your editor select a step and click on **Filter**

<figure><img src="../../../../../.gitbook/assets/Screen Cast 2022-09-08 at 3.23.47 PM.gif" alt=""><figcaption></figcaption></figure>

## How to configure it?

<figure><img src="../../../../../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

In order to use the filters you can:

* Modify the global condition from **ANY** to **ALL**
  * ANY means that if one condition is met then the line will be included in the results
  * ALL means that all conditions must be met for the line to be included in the results
* Apply condition to each lines by selecting a column, an operator and value. Depending on your column type, the available operator will change.
  * **STRING**&#x20;
  * **DATE**:
  * **NUMBERS**:
  * **BOOLEAN**:

### List of Available Operators

#### is set / is not set &#x20;

available for STRING / TIME / NUMERIC / BOOLEAN

expects no value

#### equals / does not equal

available for STRING / TIME / NUMERIC / BOOLEAN

expects one or more values

#### is in date range / is not in date range

available for TIME

expects one or more values

#### is before / is after

available for TIME

expects one or more values

#### is greater than

available for NUMERIC

expects one or more values

#### is greater or equal than

available for NUMERIC

expects one or more values

#### is lower than

available for NUMERIC

expects one or more values

#### is lower or equal than

available for NUMERIC

expects one or more values

#### contains

available for STRING

expects one or more values

#### does not contains

available for STRING

expects one or more values



When multiple values are inputed we expect the condition to match at least one of the values to return the line.
