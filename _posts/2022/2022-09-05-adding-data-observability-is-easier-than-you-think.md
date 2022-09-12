---
layout: post
title: "Adding Data Observability and Alerts to your Data Pipeline is easier than you think"
subtitle: "Add data profiling, data quality tests, and reporting to your data source in minutes"
author: Dave Flynn
date: 2022-09-05 09:00:00 +0800
background: '/img/posts/06.jpg'
featured-image: '/img/posts/data-reliability-toolkit.png'
---


After you’ve transformed the data in your data warehouse and sent it on its way, you might think that your job is done. That is, until you get a call that there’s missing data, an unexpected schema change, or some unexpected data or outlier has been introduced. To understand when these issues might have occurred, you need some form of data observability for your pipeline.

Data observability means that you can monitor the data moving through the pipeline, be alerted to any changes or issues with the data structure, and compare data to help visualize change and aid in tracking down issues.

With the open-source data observability toolkit, PipeRider, you can add data observability to your data source and start understanding more about your data in minutes with:

- Non-intrusive implementation — Focus on understanding your data without changing it
- Data profiling — In-depth analysis of the structure of your data source
- Data assertions — Ensure your data stays within acceptable ranges through testing
- Reporting — The data profile and testing results are exported to an HTML report

Following are the steps you need to get starting adding data observability and data assertions to your existing data pipeline.

## 1. Install PipeRider

PipeRider is installed via pip:

```
pip install -U piperider
```

By default it comes with SQLite, but the following connectors are also available:

- Postgres
- Snowflake
- BigQuery
- Redshift
- dbt (with one of the supported connectors)
- duckdb (coming soon)
- CSV (coming soon)
- Parquet (coming soon)

Install PipeRider with a connector like this:

```
pip install -U 'piperider[postgres,snowflake]'
```

{% youtube "https://www.youtube.com/watch?v=vZVHo09fD-c&list=PLvRlMg0l3Dq1S9KuErlgdQ8hn9LONRsHU" %}