# Why using dbt and Whaly

Dbt is a great solution widely adopted by the data community. This help you use software engineering patterns in your modeling project such as, version control through git, unit testing, continuous integration and continuous deployment. This tool has helped countless of companies scaling their modeling capabilities. But it comes at a cost.

## The problems using dbt

Like we said before dbt is a great tool, but we see two major issues with working with it.&#x20;

### Problem #1 - working as a software engineer comes at a cost&#x20;

Your people and your internal tooling must evolve to meet the new requirement that comes with this new process.

Software engineers usually all follow the same process which is:

* Getting a requirement from a business team
* Implementing the requirement on a local branch of the project
* Locally testing the new implementation
* Opening a Pull Request on your favorite git tool (github, gitlab, ...)
* Have a peer review and approve the Pull Request
* Merge the pull request
* Check production state after the pull request has been merged

&#x20;This is a complex process that has its own benefits such as:

* Each development must be approved by a peer leading to
  * A more consistent codebase
  * Less bugs pushed in production
* Each features can be tested locally leading to
  * A smoother dev experience
  * Less time spent debugging and more time spent fixing bugs and working on new features

But while this process is more robust it is very slow and can lead to fewer breakthrough in new features leading to deceptiveness from your business users standpoint. If it takes you 1 week to implement a change request, even if on the data team the confidence is increased in the capabilities to implement the change request, this will reduce the confidence in the business team that their change requests will be accounted for.&#x20;

### Problem #2 - dbt creates an organisational silo

Using dbt is a huge lead in controlling how lineage is defined and impacted, how you data can be tested and documented. But at the end of the day all those information are committed in a git repository and exposed internally under the dbt catalog feature.&#x20;

This has several implications:

* As an analyst, when I am tasked to debug a dashboard I need to rely on the dbt catalog to figure out how my dashboard is configured and how it is impacted. This requires the analyst to commit in the dbt project each dashboard configuration 😱 which is a lot to ask.
* As an analyst I cannot simply warn my users that dashboards are broken and I need to look at the results of a dbt job to understand if this failed run has any impact downstream. Asking that of the analyst is changing his role from reactive support to proactive support which is time consuming and intensive, leading to less change request implemented.&#x20;

## The solution

The Whaly X dbt integration has been design to help you close the loop between your project integrated with dbt and your business intelligence.

### Benefit #1 - Improving iteration speed

Our integration allow you to import all assets created in dbt in your Whaly project. This allow your analyst team to work in a environment to represents the state of your Warehouse. Allowing them to know which table is stale and why as well as helping them understand how those tables have been built. This helps reducing the response time for any support request and increase business adoption at the same time.&#x20;

You analyst can also leverage models and sources declared in dbt to quickly prototype new models in Whaly before moving them to dbt when they become more stable and core to your business. We noticed that the smaller the iteration time is, the bigger the business satisfaction is.

### Benefit #2 - Improving business and data teams bond

Our integration allows you to import all results associated with tests and freshness and display those information at the chart level. This helps you communicate your business users when the upstream pipeline has issues and clearly state what is impacted vs what is not. This boost confidence in your business users in using the charts stored in the BI platform while helping analyst debug faster the issue's root cause.&#x20;

## Where do we go next ?

Our main goal is to create a platform that drives business users adoption while giving the tools to data team to excel at their jobs. We have a strong belief that dbt is there for the long run and we would like to push for a deeper integration between the two platform by:

* Automatically push exploration / dashboards as Exposures in your git repository
* Let Whaly users create exploration using the dbt metric layer
* Automatically invalidate cache after a dbt run
* Integration with the dbt cli
