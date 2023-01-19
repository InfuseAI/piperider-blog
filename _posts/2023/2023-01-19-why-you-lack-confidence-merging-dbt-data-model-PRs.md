---
layout: post
title: "Why you lack confidence merging dbt data model PRs"
subtitle: "Improve the PR review process with automated metric comparisons"
author: PipeRider
background: '/img/posts/06.jpg'
hidedate: true
featured-image: '/img/posts/dbtman.jpg'
cta:
---

We love dbt - Its popularity seems to have skyrocketed over the last year or so. Everywhere I look people are writing about learning and using dbt. Applying software development practices to data projects, and the beauty of ELT, has really struck a chord with data engineers. 

With dbt projects managed in Git, data engineers can take advantage of versioning, pull requests, issues, and all the related good stuff such as continuous integration (CI) and continuous deployment (CD) to automate tasks when pull requests (PR) are made on a project. This opens the door to so much possibility for augmenting the building and deployment process with extra features.

## With great power, comes great responsibility

The power that dbt and Git/CI brings is great, and it makes collaborating on data projects so much easier, but with more engineers working together on projects, and increasing size and complexity of data pipelines, the process of reviewing data project pull requests is getting much more difficult. 

## Are you confident merging changes to production?

Reviewing a pull request already has a [laundry list of things to consider](https://www.getdbt.com/blog/how-to-review-an-analytics-pull-request/), but there’s one aspect which can be particularly difficult - Ensuring that the “[data returns expected results](https://www.getdbt.com/blog/how-to-review-an-analytics-pull-request/#-data-returns-expected-results)”, especially when you’re looking at model changes to an existing pipeline and need to determine the impact of the change.

If you can’t determine the full impact of the changes, then it’s impossible to be completely confident in merging data model changes. The amount of confidence you have depends on the method you use to check the data, and for that, you’re on your own.  

## How do you check the data?

Comparing the data from production with the data from the PR isn’t always straightforward, and it’s the part of the process when ‘silent errors’ can sneak into the pipeline, especially with [key metrics](https://docs.getdbt.com/docs/build/metrics). So, what are the common ways to check the data, and are they any good?

### Manually check

This method involves querying the data, checking values against known correct values, and generally trying to get a ‘feel’ for if the data is correct. The problem is that it’s a slow process, and manual checks are error prone. It’s too easy to miss something and have errors sneak into production. 

### BI Tools

The data ends up in BI tools anyway. Couldn’t you just check the data there? You could load the PR data into a BI tool but, again, it’s a slow process, and there’s no great way to compare production and PR environments in a BI tool.

### dbt tests

dbt has assertions that you can use to test the data in a pass/fail sense: `unique`, `not null`, `accepted values` and `relationships`.  dbt tests are useful for some cases but, for metrics, there’s no way to define what ‘correct’ data looks like. The only way to know if a change in metrics is desired is to compare metrics from the PR environment with production and then assess, given the modeling changes, if the impact of these changes are expected.

## Solution: Automated metrics comparison

> One of the many benefits of running dbt in a CI environment is being able to query the production data and see how it compares to the data built by the changes in the PR.

<p style="text-align: right">-- Erin Vaughan, Director of Customer Success @ dbt labs</p>

As Erin mentions above, a CI process is invaluable for dbt projects, and with dbt’s [state](https://docs.getdbt.com/reference/node-selection/methods#the-state-method) method ([SlimCI](https://docs.getdbt.com/guides/legacy/best-practices#run-only-modified-models-to-test-changes-slim-ci)) you can create a PR environment and [only run/test models that have changed](https://discourse.getdbt.com/t/how-we-sped-up-our-ci-runs-by-10x-using-slim-ci/2603).  

This is where our solution comes in - To automatically query and compare key metrics as part of CI/CD and provide a summary of changes for the review to quickly grasp the impact.

The CI process goes something like:

- Create a PR environment (using dbt state)
- Query key metrics from PR environment
- Query key metrics from production environment
- Compare the metrics from both environments
- **Attach a metrics comparison summary to the PR comment**


![Compare metrics](/img/posts/piperider_compare-business-metrics.png "Compare metrics with PipeRider")
<p style="text-align: center">Compare metrics using PipeRider</p>

### Confidence Acquired

The PR reviewer can now not only be alerted to model changes that affect metrics, but also see the impact of those changes. They can then determine if those changes are desirable and expected, or are the result of an error in the modeling queries. 

With this knowledge to hand, data engineers and PR reviewers can [be more confident merging data model changes into production](https://blog.infuseai.io/how-to-be-more-confident-making-data-model-changes-76a2f65feffa), and stop letting silent errors slip into production.

## PipeRider

At PipeRider, we’re already well into solving this problem and you can try out our solution right now. PipeRider is our data reliability tool with a special focus on dbt project integration and automation with CI.

- Read more about [using PipeRider with continuous intergration](https://docs.piperider.io/cli/continuous-integration-ci) in the documentation
- You can also [add dbt metrics to your PipeRider reports](https://docs.piperider.io/cli/dbt-integration/metrics), and compare metics between runs

If you’re interested in better understanding the impact of data model changes, get started with [PipeRider and dbt](https://docs.piperider.io/cli/dbt-integration), or sign-up at [piperider.io](https://piperider.io) to arrange a call.
