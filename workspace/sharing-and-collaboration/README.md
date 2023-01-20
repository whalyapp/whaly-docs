---
description: >-
  Whaly is built to be super collaborative, so there's a number of ways to share
  the dashboards you create with other people, exactly the way you want them to.
---

# ✨ Sharing & Collaboration

## Ways to share

There are several different ways you can share the reports you build in Whaly with folks inside and outside your organisation. Below is an overview of all the ways to share.

In order to manage the visibility and sharing of Reports inside Whaly, you'll have to use the Sharing configuration of the **Folders** where the Reports are stored.

{% hint style="info" %}
**All Reports stored in the same Report Folder** will be shared to the **same audience** in the same way, so if you want to have different Sharing settings for different Reports, you will have to **create different Folders** for those.
{% endhint %}

#### Share menu <a href="#share-menu" id="share-menu"></a>

First, here's a quick tour of the `Share` menu, which can be clicked when opening the `...` menu of your Report Folder.

<figure><img src="../../.gitbook/assets/Screenshot 2023-01-16 at 18.55.43.png" alt=""><figcaption><p>Share button is in the <code>...</code> menu of Report Folders</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/Screenshot 2023-01-16 at 18.56.46.png" alt=""><figcaption><p>The Share menu shows who can currently access the folder and gives control to update the sharing configuration</p></figcaption></figure>

* Each row in this menu represents a different person or group of people you can share the Folder with. In the menu above for this 'My Folder' report folder:
  * `Admins`  means that the Admins in your workspace has full access on the report. They'll be able to make edits and invite additional people.
  * `Engineering` means that all the members of the Engineering group has full access on the report. They'll be able to make edits and invite additional people.
  * `All Users` means that all members of the organization will have a read only access on the folder and its Reports.
  * `Emilien` is an exemple of a team member with only edits right on the folder. He will be able to edit the folder name and position in the folder hierarchy and edit all Reports in the folder but won't be able to change its sharing configuration.
* `Invite` lets you add people/groups inside your organization to this folder using their email address/name
  * You will be able to select the access they should have on this report

<figure><img src="../../.gitbook/assets/Screen Cast 2023-01-16 at 7.00.08 PM.gif" alt=""><figcaption><p>When inviting someone to collaborate on a folder, a permission level can be assigned to control its access</p></figcaption></figure>

#### Share with everyone in your workspace <a href="#share-with-everyone-in-your-workspace" id="share-with-everyone-in-your-workspace"></a>

You can collaborate with other people in Whaly by adding them as users to your workspace. These can be your teammates at work, partners, or anyone you want to work with on Reports. You can share Whaly reports with all members of your organizatrion so you can work together:

* In the `Share` menu, you can turn on access for `All Users` at a certain level selected from the dropdown

<figure><img src="../../.gitbook/assets/Screen Cast 2023-01-16 at 7.02.28 PM.gif" alt=""><figcaption></figcaption></figure>

#### Share with individual teammates <a href="#share-with-individual-teammates" id="share-with-individual-teammates"></a>

Sometimes you'll want to share a folder with only select other members of your organization — like a personal objective tracking dashboard you share with your manager.

* Click `Share` in a Report Folder menu.
* Click the `Add emails or people` search bar and add the members you want by typing in their name or email addresses. You can set their access levels from the dropdown at the right side of the search bar.

<figure><img src="../../.gitbook/assets/Screen Cast 2023-01-16 at 7.03.10 PM.gif" alt=""><figcaption></figcaption></figure>

#### Share with groups <a href="#share-with-groups" id="share-with-groups"></a>

To make it easier to share with commonly-used groups (i.e. your company's engineering team or sales team), you can create your own member groups and assign them permission to access reports as units.

[Learn more about groups here →](../../organisation/user-groups.md)

**Here are quick instructions for group sharing:**

* Go to `Settings > User Groups` and you'll see a list of all your already existing groups.
* Click `Create new group`, give it a name, and add the members you want
* To share a report folder with a particular group, go to `Share` in the `...` menu of this folder, then click the `Invite` button. You'll see your groups listed in the invite pop-up that appears.

<figure><img src="../../.gitbook/assets/Screen Cast 2023-01-16 at 7.03.53 PM.gif" alt=""><figcaption></figcaption></figure>

#### Share to the web <a href="#share-to-the-web" id="share-to-the-web"></a>

To make a Whaly report viewable as a site on the web or to share it with people who don't use Whaly, you can create a **Sharing Link** directly on a Report you want to share. Anyone with the link will be able to see it.

[Learn more about **Sharing Links** here →](share-a-report-by-link.md)

### Permission levels

This is where Whaly's sharing options get nuanced and granular. For every person or group you share with, you can assign a different level of access. **For example**, **this is helpful if:**

* You want only a few people to edit reports, while everyone else reads it.
* You want some reports to only be visible to a specific team.

{% hint style="info" %}
**Note:** When you invite someone to a Report Folder, they can automatically access all of its sub-folders by default. That being said, you can expand sub-folder permissions!
{% endhint %}

#### How to edit permissions <a href="#how-to-edit-permissions" id="how-to-edit-permissions"></a>

Whenever you invite someone to a Report Folder, or click on `Share`, you'll see right-hand dropdown menus next to people or groups that let you select their level of access: `Full access`, `Can edit`, and `Can view`.

* `Full access`: People with full access to a folder can edit any of the content it contains and share the folder with anyone they want using all the mechanisms in this guide.
* `Can edit`: Select this level of access for people or groups who should be able to edit the content on the folder, but not share the folder.
* `Can view`: People with this level of access can read the content on the folder, but not comment on it or edit it. They also can't share the folder with others.

<figure><img src="../../.gitbook/assets/Screen Cast 2023-01-16 at 7.07.04 PM.gif" alt=""><figcaption></figcaption></figure>

#### Stop sharing <a href="#stop-sharing" id="stop-sharing"></a>

If you have full access to a folder, you can disable sharing with anyone at any time.

* Click on `Share` in the `...` menu of the of the folder, and switch off access for your workspace, individuals, groups, or the public. You can also select `Remove` from the dropdown next to any of these.

<figure><img src="../../.gitbook/assets/Screen Cast 2023-01-16 at 7.07.36 PM.gif" alt=""><figcaption></figcaption></figure>

## FAQs

### I want to share a Report with a client, but they don't use Whaly.

You can create a [Sharing Link](share-a-report-by-link.md), and share the URL with them. They'll be able to view the report, even if they don't have a Whaly account. However, they won't be able to make any edits.
