# Configure a table

<figure><img src="../../../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

In order to configure a table you can click on one. Tables can be in error, when they do so, they are marked in red and a cross mark appears next to the table name. When hovering on the cross mark you can then view the reason of the error and correct it.

<figure><img src="../../../.gitbook/assets/image (12) (1).png" alt=""><figcaption></figcaption></figure>

## Automatic measure creation

When creating a table for a new exploration or when adding related data we prompt you the choice of adding a raw table (without any metrics or dimension) and you can create your own metrics and dimensions, or we will create them for you.&#x20;

In the case where we create the metrics and dimensions for the newly created table, we will create for each column of type Numeric and is not called `id` or does not ends with `_id` create an `average` and a `sum` metric of the column, we will also create a `count` metric for the whole table. For all the other columns we will create a dimension. If your dataset has more than 200 columns we will throw an error.
