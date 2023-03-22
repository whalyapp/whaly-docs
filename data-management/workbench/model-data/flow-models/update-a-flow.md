# Update a Flow

You can modify a Flow query whenever you want to. In order to do so, click on your Flow and go to the **configuration** tab. You should be prompted with the **Flow Editor.**

<figure><img src="../../../../.gitbook/assets/image (14) (1) (1).png" alt=""><figcaption><p>Flow editor</p></figcaption></figure>

In the flow editor there are 5 kind of actions that you can do:

1. **Select a Step**\
   ****By clicking on any blocks in the editor you can view it's output as well as the configuration of the step, this is useful for debugging and understanding the overall creation process.
2. **Edit a Step**\
   ****When clicking on a step you can edit it in the left panel, each steps has its own configuration and some might not have any customisation capabilities. Please refer to the [Flow Steps](flow-steps/) section to better understand what is available.
3. **Add a Step**\
   ****By clicking on any button in the action bar it will add a new step right after the selected one. If the selected one has already a next step the new step will be inserted in between the two existing steps.
4. **Set a Step as the Output**\
   ****A flow must have an output. The output doesn't have to be the last step in the Flow it could be any steps allowing you to continue working on your flow while not breaking its schema.
5. **Save the Flow Query**\
   ****Once you are done editing your Flow you can save it and the query will be updated right away.

### Understanding Steps

Steps have an internal state where they can be in <mark style="color:orange;">**warning**</mark> or in <mark style="color:green;">**success**</mark>. When your step configuration is not successful meaning that the SQL generated underneath contains errors then your step will be flagged as warning and a warning sign will be displayed next to it. When there is no warning sign it means that the steps is in success.&#x20;

<figure><img src="../../../../.gitbook/assets/image (9) (2).png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
Note that you cannot assign the output to a steps that has warnings and you cannot save your flow if any of the steps have warnings.
{% endhint %}

### Adding a Step

There are two ways of adding steps into the editor.&#x20;

If you want to add data then you can simply drag and drop data from your **View Selector** like you see below.&#x20;

<figure><img src="../../../../.gitbook/assets/Screen Cast 2022-09-08 at 2.44.29 PM.gif" alt=""><figcaption><p>Adding data</p></figcaption></figure>

If you want to add a step to modify data then you will need to click on the said step and add a new step by clicking on the toolbar and selecting the step you want to add.

<figure><img src="../../../../.gitbook/assets/Screen Cast 2022-09-08 at 3.01.50 PM.gif" alt=""><figcaption><p>Adding a Step</p></figcaption></figure>

{% hint style="warning" %}
Column names must only contain alphanumeric characters and you must use underscores instead of spaces. Make sure your column does start by a letter. A column name must be unique on a dataset
{% endhint %}

### Removing a Step

You can remove a step by selecting it and clicking on the red cross at the top right hand corner of the step.



<figure><img src="../../../../.gitbook/assets/Screen Cast 2022-09-08 at 2.49.06 PM.gif" alt=""><figcaption></figcaption></figure>

### Setting a Step as the output

You can set a step as the output by selecting a step and clicking on **set as output**

<figure><img src="../../../../.gitbook/assets/Screen Cast 2022-09-08 at 2.52.52 PM.gif" alt=""><figcaption><p><strong>Setting step as output</strong></p></figcaption></figure>
