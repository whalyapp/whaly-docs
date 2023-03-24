# 🏷 User Attributes

User attributes allow for personalized experiences for Whaly users. These attributes are defined by Whaly administrators and can be applied to individual users.

User attributes can be referenced throughout Whaly to provide a custom experience for each user. Looker provides several default user attributes including:

* ID
* Email

### Viewing user attributes <a href="#viewing_user_attributes" id="viewing_user_attributes"></a>

To access your user attributes, navigate to the **Access Admin > User Attribute** section of the Setting menu and select the User Attributes page.&#x20;

Here, you will find a table that displays the technical name, label, and type of each user attribute. The table also includes buttons for performing actions related to the user attribute.



### Creating user attributes <a href="#creating_user_attributes" id="creating_user_attributes"></a>

To define a user attribute, click the **Create new Attribute** button at the upper right of the screen. Each user attribute has the following settings:

* **Label**: The user-friendly name of the attribute.
* **Technical Name**: The technical name of the user attribute, that will be used in the API or in CSV users imports.
* **Data Type**: This setting is used to check that valid values are assigned to users for this user attribute. The data type of the user attribute can be one of the following:
  * **String**: Select this option to create a user attribute that exactly matches one or multiple string value, such as a username, tenant ID, ...
  * **Number**: Select this option to specify a single number, such as employee number.
  * **Date**: Select this option to specify a single date or time, such as user's birth date or a max lookback date.
  * **Boolean**: Select this option to set this attribute to be either set as True or False.
* **Allow multiple values**: Select this checkbox to allow users to have multiple values for the attribute. It can be useful if you want some manager to have access to multiple Sales region for example.
* **Allow only specific values**: Select this checkbox to pass the allowlist of authrorized values that can be given for this attribute to user.
* **Set a default value**: Select this checkbox to set a default value in case a value is not assigned to a user.

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

### Assigning values to individual users <a href="#assigning_values_to_individual_users" id="assigning_values_to_individual_users"></a>

After defining a user attribute, you can assign a value for it to an individual user:

1. Go to the Settings > Access Admin > **Access Management** page.
2. Choose the user to assign a value and click on "Edit User"
3. In the Attributes section, enter the new value in the proper field.
4. Click **Save**.

<figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

### Where can user attributes be used? <a href="#where_can_user_attributes_be_used" id="where_can_user_attributes_be_used"></a>

#### Reports Filters

Filters on reports can be set to a user attribute to customize the query based on the user who is running it.

For example, you could configure a user attributes named "salesforce\_username" and customize it for every Whaly user by entering their Salesforce username as its value. By setting a filter on a dashboard using the "salesforce\_username" user attribute, each user would be able to view the dashboard with data filtered according to their particular Salesforce username.

