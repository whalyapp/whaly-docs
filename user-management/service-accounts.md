---
description: >-
  Service accounts are technical users used to authenticate API integrations
  between Whaly and external systems and applications.
---

# 🤖 Service Accounts

## Service Account Documentation

### Introduction

Service accounts are technical users used to authenticate API integrations between Whaly and external systems and applications. They provide a secure way to access Whaly APIs without relying on individual user credentials. This documentation aims to provide an overview of how to use Whaly service accounts, their purpose, benefits, and guidelines for managing and using them effectively.

Unlike user accounts, service accounts are not associated with individual users and do not have interactive login capabilities. They are designed to perform automated tasks in Whaly (create User Accounts on the fly, download data, etc.) to bridge your internal systems with Whaly.

### 1. Purpose and Benefits

The use of service accounts offers several advantages:

* **Secure Authentication:** Service accounts provide a secure method for authenticating API requests through Keys without exposing user credentials or relying on manual authentication steps.
* **Resilient to Users updates**: People join and leave your organization all the time. Linking an integration to a User account create the risk that the integration can break whenever the linked User account change its permissions or is disabled. By relying on Service Accounts instead, your integrations are less encline to break.
* **Granular Control:** Service accounts can be granted specific roles and access controls, allowing fine-grained control over the actions they can perform on Whaly APIs.
* **Auditability:** Service accounts enable logging and auditing of API requests and tie them with the Service Account name, providing an audit trail for monitoring and troubleshooting purposes.

### 2. Creating a Service Account

In order to create a Service Account, you have to go to the Service Account panel in the Settings of your organization.

<figure><img src="../.gitbook/assets/image (4) (5) (1).png" alt=""><figcaption></figcaption></figure>

From this screen, you can see the already existing Service Accounts and create new ones to authenticate a new Integration. You have to click on the "Create Service Account" button to do that.

<figure><img src="../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

In the panel that appears, you can:

* Give the proper name to the Service Account so you identify it and how it's being used later one when reviewing your open access. Make sure to use a descriptive name.
* The Role that this Service Account should have on your Organization. This will impact the API that the Service Account will be able to access.

Once it's done, you can click on "Submit" to create the Service Account.

<figure><img src="../.gitbook/assets/image (1) (1) (2).png" alt=""><figcaption></figcaption></figure>

When creating a new Service Account, a Key is automatically attached to it and you can copy paste the associated API Token that will be used to authenticate as this Service Account through the API.

{% hint style="info" %}
The value of the API Token is only available on the Key creation time, so be sure to cpy and store in a safe place its value because it won't be available in Whaly interface after that.

If you lose the API Token, you can always create a new Key on the existing Service Account to get a fresh API TOken.
{% endhint %}

### 3. Service Account Keys

Each Service Account can hold many Keys. Those Keys are attached to a API Token that is the value to be used when authenticating against the API.

In order to manage Keys, you can click on the "..." icon on a Service Account row and click on "Manage Keys".

<figure><img src="../.gitbook/assets/image (2) (1).png" alt=""><figcaption></figcaption></figure>

From this screen, you can list the already existing keys, view an obfuscated value of their API Token and either remove existing Keys or create new ones.

### 4. Best Practices for Service Account Management

To ensure effective management and security of your service accounts, consider the following best practices:

* **Naming Conventions:** Establish a consistent naming convention for each service accounts, enabling easy identification and categorization based on their purpose and associated systems.
* **Regular Review and Maintenance:** Perform regular reviews of existing service accounts and their Keays to ensure they are still required and have appropriate permissions. Remove or revoke unnecessary or unused service accounts promptly.
* **Rotation of Keys:** Implement a regular rotation policy for service account keys to mitigate the risk of compromised credentials.
* **Least Privilege Principle:** Adhere to the principle of least privilege when granting permissions to service accounts. Only assign the minimum necessary permissions required for their intended functionality, reducing the potential impact of a compromised service account.
* **Documentation and Ownership:** Maintain accurate documentation of service accounts, including their purpose, associated systems or applications, and responsible owners. This documentation ensures clear accountability and facilitates efficient management.

\
