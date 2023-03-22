# Where should my models be managed?

There are many great solutions widely adopted by the data community to build and manage your business knowledge through Models such as dbt, Keboola and Dataform. Such tools have helped countless of companies scaling their modelling capabilities.

Those solutions help you use software engineering patterns in your modelling project such as:&#x20;

* documentation
* version control through git
* unit testing
* source freshness
* continuous integration
* continuous deployment
* templatization engine

In the same time, Whaly offers a lightweight modelling layer that enable people to build:

* SQL models
* Flow Models (no-code)&#x20;

In the end, successful data architecture contains Models in both specialised modelling solutions and in Whaly in the same time, let's dive in to understand why Whaly models exists.

## Working as a software engineer comes at a cost

The reason why modern modelling solution are so good is that they took inspiration of the Software engineering best practises. But it is also one of their biggest issue.

When you switch to a code based modelling layer, your people and your internal tooling must evolve to meet the new requirement that comes with the "software engineering" process.

{% hint style="info" %}
As a reminder, the common "Software engineering" process is:

1. Getting a requirement from a business team
2. Implementing the requirement on a local branch/copy of the project
3. Locally testing the new implementation
4. Opening a Pull Request on your favorite git tool (github, gitlab, ...)
5. Have a peer review and approve the Pull Request
6. Merge the pull request
7. Check production state after the pull request has been merged
{% endhint %}

&#x20;This is a powerful but complex process that has its own benefits such as:

* Each development must be approved by a peer leading to
  * A more consistent codebase
  * Less bugs pushed in production
* Each features can be tested locally leading to
  * A smoother dev experience
  * Less time spent debugging and more time spent fixing bugs and working on new features

But while this process is more robust, it is quite slow and requires the use of a lot of tools (git, CI/CD, etc.) which means that fewer people can follow it because of lack of skills and time.

In the end, it lead to fewer and slower data breakthroughs, leading to deceptiveness from your business users standpoint.

## What are Whaly models and how they complete models managed by an external solution

Whaly models are lightweight and easy to create. SQL knowledge is not even required as they also exists in a visual "flow" fashion. This way, it's very easy for anyone in your organisation to create and share their own Models, similar to what they could do with a spreadsheet.

In the same time, those lightweights models can be used and shared inside Whaly in the same way as a Modelling solution model could be used: in the end, the produced dashboards looks the same.

Whaly models can be individually "migrated" to the specialised solution once your organisation wants to get a better level of control over them.

## Summary

| Model type                    | Pros                                                                                                                    | Cons                                                                                                    | When to use                                                                                                                                                                            |
| ----------------------------- | ----------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Whaly models                  | <ul><li>Easy/fast to create for anyone</li><li>Exists in code (SQL) or no-code way</li></ul>                            | <ul><li>Can result in "fragile" data hierarchy</li><li>No strong governance on Models changes</li></ul> | <ul><li>When prototyping a data project</li><li>When working with business users (Product Managers, SalesOps, RevOps)</li></ul>                                                        |
| dbt, Keboola, Dataform models | <ul><li>Comes with a very mature process to produce high quality models</li><li>Very extensible (macros, ...)</li></ul> | <ul><li>Slow/costly to create</li><li>Only come as code (SQL/Python)</li></ul>                          | <ul><li>When industrialising a project</li><li>When a model is important and data quality matters</li><li>For slow changing models, once the business requirements are clear</li></ul> |

