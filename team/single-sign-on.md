# 🛡 Single Sign On

Whaly supports Single Sign On. This means that you can plug your existing Identity Provider such as Google Workspace, Microsoft Azure Directory, Okta, custom SAML ... into Whaly so that your Team Member have to login through your company identity system before accessing Whaly.

This offers multiple advantages:

* When your IT team disable a User in your company directory, the User no longer can access Whaly
* Your IT team can decide form your Directory which User should have access to Whaly or not
* Your Team Members passwords are never known / saved into Whaly systems
* Whaly will create users "on the fly" when they first login. This means that you don't have to create any Whaly access for your new team members or invite your whole company before they can get access

Overall, enabling Single Sign On is:

* More secure
* Give you more control
* Lower the user management cost for your IT Team
* Offer a better login experience to your Team Members
* In many case, this is required if your company is security certified (SOC2 / ISO27001)

In order to configure your SSO, you simply have to go to your [Team Management](what-is-a-team.md#managing-the-team) page and click on "Configure my SSO". You'll be redirected to a portal where you can self configure your SSO Provider.

{% hint style="info" %}
If your current plan doesn't include SSO support, a link to contact Whaly Sales team will be displayed so that you can discuss about your needs.
{% endhint %}

### User provisioning

Whenever a new User from your company directory is logging for the first time into Whaly, a new User will be created on the fly and a Viewer (free) access will be created on the Organizations of your team.

The Administrators of your [Organizations](broken-reference) will then be able to assign the proper [access](../organization/manage-access-control.md) and [licenses](../organization/understanding-licences.md) to them.

## Supported Identity Providers

Whaly currently supports the following Identity Providers:

<figure><img src="../.gitbook/assets/Screenshot 2022-10-14 at 12.50.12.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Thanks to our generic SAML support, we can also connect to Identity providers that are not included in the list.

Contact your support if you need assistance!
{% endhint %}
