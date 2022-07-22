---
description: >-
  This page explain you how you can manage which user of your org can have
  different rights on Whaly.
---

# 👮 Access Control

### User Roles

There are four different user roles in [Whaly](https://whaly.io).

#### Admin Builder

An admin builder can view / edit / delete everything. Meaning that he has the ability to:

| object       | right                            |                                                                                                                                |
| ------------ | -------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| Users Invite | Read / Create                    | An **admin builder** can invite whoever he wants in the org and give them the appropriate role                                 |
| User Roles   | Read / Create / Update / Delete  | An **admin builder** can change any user role to the role he judges the most appropriate                                       |
| Sources      | Read / Connect / Update / Delete | An **admin builder** can connect any source to its org and remove sources that were previously connected or change the config. |
| Explorations | Read / Create / Update / Delete  | An **admin builder** can create, read, modify and remove any exploration                                                       |
| Workbench    | Read / Create / Update / Delete  | An **admin builder** can access the workbench, create, remove columns and add formulas, rollups, and lookups                   |
| Reports      | Read / Create / Update / Delete  | An **admin builder** can create, read, modify and remove any reports                                                           |



#### Builder

A builder has essentially the same rights as an owner except for user management.&#x20;

| object       | right                            |                                                                                                                         |
| ------------ | -------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| Users Invite | Read                             | A **builder** can view invitations but cannot invite a user.                                                            |
| User Roles   | Read                             | A **builder** can view user roles but cannot modify them                                                                |
| Sources      | Read / Connect / Update / Delete | A **builder** can connect any source to its org and remove sources that were previously connected or change the config. |
| Explorations | Read / Create / Update / Delete  | A **builder** can create, read, modify and remove any exploration                                                       |
| Workbench    | Read / Create / Update / Delete  | A **builder** can access the workbench, create, remove columns and add formulas, rollups, and lookups                   |
| Reports      | Read / Create / Update / Delete  | A **builder** can create, read, modify and remove any reports                                                           |

#### **Editor**

An editor can create reports in the org, and has access to explorations and reports. He has the ability to:

| object       | right                            |                                                                                  |
| ------------ | -------------------------------- | -------------------------------------------------------------------------------- |
| Users Invite | Read                             | An **editor** can view invitations but cannot invite a user.                     |
| User Roles   | Read                             | An **editor** can view user roles but cannot modify them                         |
| Sources      | Read / Connect / Update / Delete | An **editor** can view connected sources but cannot modify them.                 |
| Explorations | Read / Create / Update / Delete  | An **editor** can view explorations, can run queries but cannot modify anything  |
| Workbench    | Read / Create / Update / Delete  | An **editor** doesn't have access to the workbench                               |
| Reports      | Read / Create / Update / Delete  | A **builder** can create, read, modify and remove any reports                    |

#### **Viewer**

A viewer cannot edit anything in the org, but has access to explorations and reports. He has the ability to:

| object       | right     |                                                                                 |
| ------------ | --------- | ------------------------------------------------------------------------------- |
| Users Invite | Read      | A **viewer** can view invitations but cannot invite a user.                     |
| User Roles   | Read      | A **viewer** can view user roles but cannot modify them                         |
| Sources      | Read      | A **viewer** can view connected sources but cannot modify them.                 |
| Explorations | Read      | A **viewer** can view explorations, can run queries but cannot modify anything  |
| Workbench    | no access | A **viewer** doesn't have access to the workbench                               |
| Reports      | Read      | A **viewer** can access reports but cannot modify nor delete them               |

#### **Report Viewer**

A report viewer cannot edit anything in the org, and has only access to reports. He has the ability to:

| object       | right     |                                                                          |
| ------------ | --------- | ------------------------------------------------------------------------ |
| Users Invite | Read      | A **report viewer** can view invitations but cannot invite a user.       |
| User Roles   | Read      | A **report viewer** can view user roles but cannot modify them           |
| Sources      | Read      | A **report viewer** can view connected sources but cannot modify them.   |
| Explorations | No access | A **report viewer** doesn't have access to explorations                  |
| Workbench    | No access | A **report viewer** doesn't have access to the workbench                 |
| Reports      | Read      | A **report viewer** can access reports but cannot modify nor delete them |
