# General Information

## Displaying dataset information

You can display the dataset information by opening any dataset and going to the **information** tab

<figure><img src="../../../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>

### Name & description

In this tab you can edit the dataset name as well as the dataset description. Creating clear names and description are crucial for proper maintenance and scalability of the project. Gather up with your team and decide on a taxonomy to adopt

### Schema

The schema block allow you to manage primary keys but also to view the output of the schema with all primary keys an foreign keys.

Learn more on how to manage primary keys

{% content-ref url="primary-keys.md" %}
[primary-keys.md](primary-keys.md)
{% endcontent-ref %}

### Relationships

Learn more on how to manage relationships here:

{% content-ref url="relationships.md" %}
[relationships.md](relationships.md)
{% endcontent-ref %}

### Delete

You can delete a dataset by **hovering** it in the **View Selector** under **Model** and clicking on the **three dots** or by clicking on the delete button in the **information** tab.

{% hint style="info" %}
Be careful when deleting a model this might break explorations that are using is or models it has been referenced in.
{% endhint %}

{% hint style="warning" %}
You cannot delete datasets that are managed by Whaly (meaning datasets created by the third party sources) In order to delete those datasets stop syncing them in the source panel.
{% endhint %}
