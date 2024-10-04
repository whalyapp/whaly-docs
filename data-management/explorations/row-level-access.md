# Row Level Access

Row Level Access (RLA) allows Builders to control which rows of data each user can access, based on specific attributes configured at the user level. This ensures that users only see data relevant to their role, location, or other designated criteria. The feature enhances data security and personalization by filtering data dynamically per user.

Row Level Access is configured at the "Exploration" level. RLA binds a specific dimension within an [Exploration](./) (e.g., "Country") to a [User Attribute](../../user-management/user-attributes.md), allowing for granular control over the data a user can see in that context.

To implement RLA, you bind a dimension in the [Exploration](./) to a [User Attribute](../../user-management/user-attributes.md). A dimension is a field in the dataset, such as "Country," "Department," or "Team." The [User Attribute](../../user-management/user-attributes.md) is configured at the user level and determines what value the user has for that dimension. For example, if the "Country" dimension is bound to a User Attribute "user\_country," users will only see rows where the "Country" matches their "user\_country" value.

Example:

* **Dimension:** Country
* **User Attribute:** user\_country
* **Outcome:** A user with "user\_country = USA" will only see rows where "Country = USA."

<figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

### **FAQs**

#### **Q1: How do I troubleshoot RLA configuration issues?**

Ensure that the correct [User Attributes](../../user-management/user-attributes.md) are assigned to users and that the dimension in the Exploration is properly bound to the User Attribute. Check that users have the necessary attribute values set. You can use [User Impersonation](../../team/impersonate.md) to validate the setup.

#### **Q2: What happens if a user doesn’t have a User Attribute set?**

#### If a User Attribute is not set, the user will see no data for security reasons. So it's important to properly configure the [User Attribute](../../user-management/user-attributes.md) of each users.

#### **Q3: I want some users to see all available data**

The `*` value can be used in [User Attribute](../../user-management/user-attributes.md) value to indicate that the user can see everything.
