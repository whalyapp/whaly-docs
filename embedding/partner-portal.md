# 🪟 Partner Portal

In order to offer a branded experience to your Business Partners (customers, lead partners, investors, etc.), Partner Portal gives you the ability to create a tailor made experience. Partner Portal are providing:

* A customisable login page
* A dedicated user management system
* The ability to customise the Homepage

## Creating a Portal

In the **Settings > Partner Portal** page, click on "Create new Portal" to open the Portal creation form.

<figure><img src="../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

You'll need to fill the following information:

* **Name**: This is the display name of the Portal as it will appear in the login page and once users have logged in in the portal.
* **Technical name**: This will be used to build the URL of the portal, in the `https://<technical-name>.portals.whaly.io/` format
* **Color**: This will be used to theme the Login page background
* **Logout URL**: When user are logging out from the portal, this is the URL they will be redirected to.
* **Default home cover** (optional): If you want to customize the Home cover that people will see when they login, this is the image that will be used

At the bottom of the page, you can see the previews of how your Portal will look like based on your current configuration.

## Exposing dashboards to Portal users

When the Portal is created, a dynamic [User Group](../user-management/user-groups.md) is automatically created. It'll contain all Portal Users. You can see its name in the Portal page.

<figure><img src="../.gitbook/assets/image (2) (1).png" alt=""><figcaption></figcaption></figure>

To give access to a Report Folder that you want to expose in the Portal, you simply have to grant access to the Folder using the [Sharing menu](../workspace/sharing-and-collaboration/).

## Manage users having access to the Portal

To invite users to get access to the Portal, you should go to: Settings > Partner Portal and then click on the Portal name.

Once you are in the Portal page, you can list the users that have access to the Portal and invite them.

### Individual invitation

By clicking on the **Invite Partner** button, you can enter the Partner information:

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

**Role**: This will be the role that will define what the User will be able to do in the Portal. You can either create a "View only" experience by giving Report Viewer role to your Partners or build a more interactive experience by giving them the Editor role that will give them the ability to create their own dashboards.

**Email**: This will be the email on which the Invite will be sent

**Attributes** (optional): If you have any [User Attributes](../user-management/user-attributes.md) configured, you will be able to fill them for the current Partner here. This will be useful if you want different Partners to see different data when accessing the dashboards. Ex. you could have a "Tenant ID" for each partner so that they can only see the data relevant to them

### Mass invites / edits

As your number of Partners can grow quickly, you can also open the "Bulk update users" tool that will give you the ability to upload a CSV with all Partner information.

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

This will give you the ability to mass invite or mass edit existing Partners.

#### API Partner management

(Coming in April 2023)
