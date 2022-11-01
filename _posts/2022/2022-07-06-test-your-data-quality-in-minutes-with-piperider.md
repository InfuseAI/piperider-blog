---
layout: post
title: "Test your data quality in minutes with PipeRider"
subtitle: "Data reliability just got even more reliable with better dbt integration, data assertion recommendations, and reporting enhancements."
author: PipeRider
background: '/img/posts/06.jpg'
hidedate: true
featured-image: '/img/posts/220706-1.png'
cta: 
---

# Test your data quality in minutes with PipeRider


**tl;dr** If you missed out on PipeRider's initial release, then now is a great time to take it for a spin. **Data reliability just got even more reliable with better dbt integration**, data assertion recommendations, and reporting enhancements. PipeRider is [open-source](https://github.com/InfuseAI/piperider) and easy to [get started](https://docs.piperider.io/quick-start?utm_source=blog&utm_medium=20220706&utm_id=medium).
  
## PipeRider Recap

PipeRider is your open-source data reliability toolkit that connects to your existing data pipelines and provides data profiling, data quality assertions, convenient HTML reports, and integration with popular data warehouses. [Read more](https://blog.infuseai.io/data-reliability-automated-with-piperider-7a823521ef11) about the story behind PipeRider's creation.

![test your data quality within minutes](/img/posts/220706-2.png)

## What's New?

Recent updates to PipeRider include the following features:

-   [Recommended data assertion generation](https://blog.infuseai.io/test-your-data-quality-in-minutes-with-piperider-91da57a5c5d5#31b3) --- PipeRider's intelligently generated assertions give you a head-start on data reliability.
-   [Improved dbt integration](https://blog.infuseai.io/test-your-data-quality-in-minutes-with-piperider-91da57a5c5d5#7d35) --- PipeRider will auto-detect your dbt project and data source settings. You can also run dbt tests with PipeRider and dbt test results are included in your report.
-   [Improved reporting](https://blog.infuseai.io/test-your-data-quality-in-minutes-with-piperider-91da57a5c5d5#7511) --- Automatically generated reports provide data profiling information and assertion results.

Let's take a deeper dive into these new features.

## Recommended assertions

The first time you run PipeRider and your data is profiled, PipeRider will offer to generate recommended assertions based on the profile of your data source.

PipeRider analyzes the contents of your data source and makes intelligent suggestions based on the content, such as:

-   Asserting which columns require data and should not be null
-   Asserting the schema type for columns
-   Asserting the acceptable range of minimum and maximum values for numerical columns

![PipeRider's CLI tool offers to generate recommended data assertions based on your data profile](/img/posts/220706-3.png "Generate recommended assertions with PipeRider on first run")

By using the recommended assertions you give yourself a head start by not having to manually write all of the assertions. Instead, you can tweak and add to the recommendations if necessary.

![An example of a recommended assertions file generate by PipeRider, a data reliability tool](/img/posts/220706-4.png "Example of PipeRider's recommended assertions for a data source")

If you'd rather not use the recommendations, PipeRider can also generate empty assertion template files, complete with column names, ready for you to customize with [built-in assertions](https://docs.piperider.io/data-quality-assertions/assertion-configuration), or your own [custom assertions](https://docs.piperider.io/data-quality-assertions/custom-assertions).

## dbt integration

You can now initialize PipeRider inside your dbt project, this brings PipeRider's profiling, assertions, and reporting features to your dbt models.

![PipeRider auto-detects your dbt project settings which makes adding data profiling to a dbt project easy](/img/posts/220706-5.png "PipeRider auto detects your dbt project settings")

PipeRider will automatically detect your dbt project settings and treat your dbt models as if they were part of your PipeRider project. This includes -

-   Profiling dbt models.
-   Generating recommended assertions for dbt models.
-   Testing dbt model data-profiles with PipeRider assertions.
-   Including dbt test results in PipeRider reports.

![PipeRider can run both dbt tests and PipeRider's own assertions with one command](/img/posts/220706-6.png "PipeRider and dbt tests can be run with one command")

You can also build your dbt models using PipeRider, which means it's possible to condense your dbt and PipeRider workflow to one command: `piperider run --dbt-build --dbt-test`. This one command will:

1.  Build your dbt models.
2.  Profile your data with PipeRider's profiler.
3.  Run your dbt tests.
4.  Test your data profile with PipeRider assertions
5.  Generate an HTML report.

Full details and other available options can be found in the [command reference](https://docs.piperider.io/piperider-cli).

## Improved reporting

Reports are now automatically generated each time you run PipeRider and include the following information.

-   All tables included
-   Per-table profiling data
-   Per-table test results
-   Per-table dbt test results

### Report overview

The report overview page shows a quick view of which tables or dbt models have been profiled and tested, along with stats about passed and failed tests.

![PipeRider report overview showing both PipeRider assertion results and dbt test results](/img/posts/220706-7.png "PipeRider report overview showing both PipeRider assertion results and dbt test results")



### Per-table reports

Click through to each table to view the data profile detailed test results for that table.

![View detailed per-table information on data profile and test results in PipeRider's report](/img/posts/220706-6.png "PipeRider data table report features data profile and test results")


### dbt test results

If the PipeRider is run on a dbt project, then the report will include a tab with details of dbt-specific test results.

![View dbt test results in your PipeRider report](/img/posts/220706-8.png "View dbt test results in your PipeRider report")



### Compare reports

Two reports can also be compared showing the differences between the data profile for each run, together with the expected and actual results for each test.

![Compare results for two PipeRider runs that shows the difference in data profile and test results](/img/posts/220706-9.png "Compare two reports from different PipeRider runs")


### No excuse for unreliable data

PipeRider is so easy to use there really is no excuse for not picking up on that data drift. All you need to do it:

1.  [Install PipeRider](https://docs.piperider.io/install-piperider) (a quick install with pip)
2.  Point it to your data warehouse --- if you're using dbt your settings will be auto-detected
3.  With one [command](https://docs.piperider.io/piperider-cli) you can generate a data profile, with suggested assertions, and output a report

Check out the [quick-start guide](https://docs.piperider.io/quick-start?utm_source=blog&utm_medium=20220706&utm_id=medium), which includes a sample dataset, for how to use the main features of PipeRider.

## More info

For help using PipeRider, or if you have ideas how we can make it better, get in touch via:

-   InfuseAI [Discord community](https://discord.gg/328QcXnkKD)
-   [@infuseai](https://twitter.com/InfuseAI) on Twitter
-   ⭐️ Star us on [Github](https://github.com/InfuseAI/piperider)

## Want to learn more about data quality? 
You may also like to read: 
* [Data Reliability Automated with PipeRider](https://blog.piperider.io/data-reliability-automated-with-piperider.html)
* [Guide to Data Reliability](https://blog.piperider.io/guide-to-data-reliability.html)