---
layout: post
title: "Building Reliable Data Oipelines With Profiling and Assertions"
subtitle: "By using data profiling the task of building and maintaining reliable data pipelines is a lot more manageable"
author: PipeRider
background: '/img/posts/06.jpg'
hidedate: true
featured-image: '/img/posts/221019-0.webp'
cta: cta_2.html
---

The process of creating a data pipeline involves taking data from various sources and transforming it to make it useful for specific analytical and/or business purposes. It sounds easy enough but, with increasingly complex pipelines, errors can easily go unnoticed.

Creating error-free data pipelines takes a lot of effort from data engineers, but by using data profiling the task of building and maintaining reliable data pipelines is a lot more manageable.

<hr /> 

## Data profiling and assertions for quality assurance
The metrics that data profiling provides can be used to ensure that data meets the requirements it’s intended for, and also enables you (the data engineer) to spot anomalies or anything out of the ordinary. Essentially providing a layer of quality assurance to the pipeline.

When paired with data assertions, the profile can be tested to ensure that metrics are within desired thresholds. This is not only useful for building the pipeline, but also for continued testing throughout the life of the pipeline. Data profiling is an essential part of creating a dedicated data monitoring pipeline so you can become [‘master of your pipeline’](https://blog.piperider.io/data-monitoring-be-the-master-of-your-pipeline.html).

## 　
## Add data profiling and assertion to your ELT pipeline
The idea is to augment the ELT process with two new stages — profiling, and assertions, creating (drum-roll) ELTPA. In this updated process, a testing loop occurs during the pipeline creation to help ensure that the resulting data is robust and reliable, and then continually once the pipeline is in use.

The following diagram demonstrates the process.
![](/img/posts/221019-1.webp)

## 　
## Pipeline creation
After data is transformed, it is profiled and tested with assertions. You can write assertions based on stakeholder requirements or, if you are modifying an existing pipeline, then you may already be aware of common issues.

If an assertion fails and generates an error, you can go back to the transformation phase and find the root cause of the problem before continuing the process.

## 　
## Pipeline monitoring and observability
For continual monitoring, a data profile should also be regularly generated. If the data profile metrics reveal a change in data that needs investigation, you can compare the most recent report with previous reports to see what might have happened.

After the issue is resolved, you can update the data assertions to account for the issue and ensure that testing covers similar situations going forward.

## 　
## Conclusion
A data profile is useful for creating the data pipeline and, when generated regularly, can also be used for monitoring data distribution over time and debugging issues. The addition of assertions makes it a great way to test for data reliability. In many cases, a data profile report can reduce the need for a complex BI dashboard.

If you like this article, it’s a big encouragement to give us a like on [Twitter](https://twitter.com/InfuseAI/status/1582733321594753024?s=20&t=Nw2rTYJOoFJAWdNIdMTxfw).


## 　
### Add data profiling to your data reliability strategy
[PipeRider](https://piperider.io/?utm_source=piperiderblog&utm_medium=blog) is an open-source data reliability CLI tool that adds data profiling and assertions to data warehouses such as BigQuery, Snowflake, Redshift and more. Data profile and assertions results are provided in an HTML report each time you run PipeRider.



