---
layout: post
title: "Adding Data Observability and Alerts to your Data Pipeline is easier than you think"
subtitle: "Ensuring Data Quality with Data Observability"
author: PipeRider
background: '/img/posts/06.jpg'
hidedate: true
featured-image: '/img/posts/data-reliability-toolkit.webp'
cta: cta_2.html
---

After you’ve transformed the data in your data warehouse and sent it on its way, you might think that your job is done. That is, until you get a call that there’s missing data, an unexpected schema change, or some unexpected data or outlier has been introduced. To understand when these issues might have occurred, you need some form of data observability for your pipeline.

Data observability means that you can monitor the data moving through the pipeline, be alerted to any changes or issues with the data structure, and compare data to help visualize change and aid in tracking down issues.

<hr /> 

With the open-source data observability toolkit, [PipeRider](https://piperider.io/?utm_source=piperiderblog&utm_medium=blog), you can add data observability to your data source and start understanding more about your data in minutes with:

Non-intrusive implementation — Focus on understanding your data without changing it
Data profiling — In-depth analysis of the structure of your data source
Data assertions — Ensure your data stays within acceptable ranges through testing
Reporting — The data profile and testing results are exported to an HTML report
Following are the steps you need to get starting adding data observability and data assertions to your existing data pipeline.

## 1. Install PipeRider
PipeRider is installed via pip:
```
pip install -U piperider
```

{% youtube "https://www.youtube.com/watch?v=vZVHo09fD-c" %}

By default it comes with SQLite, but the following connectors are also available:

* Postgres
* Snowflake
* BigQuery
* Redshift
* dbt (with one of the supported connectors)
* duckdb 
* CSV 
* Parquet 
  
Install PipeRider with a connector like this:
```
pip install -U 'piperider[postgres,snowflake]'
```
## 　  
## 2. Initialize a PipeRider project
Once installed, initialize a new project with the following command.

```
piperider init
```

{% youtube "https://www.youtube.com/watch?v=jRxZQJoMQGc" %}

Just select your data source, enter the relevant details and you’re ready to go. dbt project settings will be auto-detected, so dbt projects really are zero config!

Verify your connection settings with the diagnose command.

```
piperider diagnose
```
## 　  
## 3. Run PipeRider
With a data source connected you’re ready to run PipeRider. 

```
piperider run
```

{% youtube "https://www.youtube.com/watch?v=Y9KIqu2DOsg" %}

This one command will do the following:

* Profile your data source
* Generate recommended data assertions (on first run)
* Test the data profile against the data assertions
* Display the data assertion test results on the CLI
* Generate an HTML report with the data profile and test results

## 　    
## 4. Test your PipeRider data profile with data assertions
PipeRider creates a set of recommended assertions based on the current state of your data. You can add to or edit these using the available suite of [built-in assertions](https://docs.piperider.io/cli/data-quality-assertions/assertion-configuration), and through custom assertions you can [create your own data reliability tests](https://blog.piperider.io/define-your-own-data-quality-tests-in-piperider.html).

{% youtube "https://www.youtube.com/watch?v=t4YHkynRIpI" %} 

## 　  
## 5. Compare data profile reports
When your data changes and you have multiple PipeRider runs, compare reports easily with the following command.

```
piperider compare-reports
```

{% youtube "https://www.youtube.com/watch?v=COohk2TAiPA" %} 

You can also compare the last two reports automatically (without needing to manually select them) by using the `--last` flag.

```
piperider compare-reports —last
```

## 　  
## Sample Reports
Links to example reports will always be available in the PipeRider documentation. Here are samples created with PipeRider 0.7:

[Sample PipeRider data profile report](https://piperider-github-readme.s3.ap-northeast-1.amazonaws.com/run-0.7.0/index.html#/)
[Sample PipeRider report comparison](https://piperider-github-readme.s3.ap-northeast-1.amazonaws.com/comparison-0.7.0/index.html)

## 　  
--- 
## Who makes PipeRider?
[PipeRider](https://piperider.io/?utm_source=piperiderblog&utm_medium=blog) is developed by [InfuseAI](https://infuseai.io/), the company behind the end-to-end machine learning platform [PrimeHub](https://www.infuseai.io/primehub-ai-platform).

InfuseAI has an impressive [portfolio of open-source projects](https://github.com/InfuseAI/) so you know you’re in good hands!



