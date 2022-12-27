---
layout: post
title: "Data Monitoring — Be the Master of Your Pipeline"
subtitle: "Setting up a dedicated monitoring Pipeline"
author: PipeRider
background: '/img/posts/06.jpg'
hidedate: true
featured-image: '/img/posts/221018-0.webp'
cta: cta_2.html
---

Data pipelines have evolved from a single series of workloads (or DAG within a system), to more abstract semantics with a mix of orchestrated workflows, internal tools, in-warehouse transformations and 3rd party tools exports or ingestion.

The increasing complexity of data pipelines makes monitoring difficult, to implement an effective data monitoring strategy you need to understand the pipeline completely. This could range from tracking the status of pipeline tasks and setting up alerts, right up to being the ultimate “master of your pipeline” by setting up a dedicated monitoring pipeline with metrics.

<hr /> 

## Data monitoring is essential
Once your data pipeline reaches a certain complexity, the requirement for some kind of monitoring is unavoidable. When you get the call (hopefully monitoring can help you avoid the call) that a dashboard is broken because data isn’t being updated, if you’ve got the pipeline metrics available you’ll know where to look first.

### Understand what’s happening
In its basic form, data monitoring means that you understand what’s happening in the pipeline. Start with understanding the normal execution time for tasks in your data pipelines, then set up SLAs that will raise alerts when they fail.

If you find that individual tasks are hanging, you might set up monitoring for each task separately, and then trigger an alert once a certain time threshold has been exceeded.

### How long is too long?
How you determine what is a “normal” amount of time for tasks in your pipeline to execute will differ for each case. This is where some sleuthing on your part is required. You’ll need to track the execution time and then work out what is acceptable

Some data warehouses offer execution statistics and, if you use a data monitoring service, check if event logs are available that will contain lots of metadata about your task executions.

Writing tests for each pipeline can be an extensive task, and it requires a lot of effort to maintain. At some point you might consider a more structured approach.

## 　
## Take it to the next level
To get serious about your data monitoring, you can set up a dedicated pipeline for monitoring metrics. In these more complex data monitoring efforts, you can monitor many metrics and set up alerts for each kind of metric.

### What should you monitor?
Examples of metrics to monitor could include things like -

* Data freshness
* Schema types
* The number of rows in a table
* The number of inserted rows
* The percentage of null values
* The acceptable range of values
* The distribution of data

The type of metrics you monitor will depend on a mix of what is important to the stakeholder, what issues you are running into on a regular basis and, of course, metrics that you need to monitor to ensure that the pipeline is functioning.

### What are the acceptable thresholds?
Once you know the metrics that need to be monitored, you need to figure out acceptable thresholds for these metrics. This will either involve asking the stakeholder, or employing some form of data profiling so you can track the metric over time and determine acceptable values and/or ranges.

## 　
## Conclusion
The complexity of the data monitoring solution you employ will be based on the complexity of your pipeline. I’ve mentioned a few methods that you might use to monitor your data pipelines, but there are many more things to monitor — I’ve not even touched on business logic as that introduced a whole other set of complexity.

What methods are you using for monitoring your data pipelines?

How do you determine what are the important things to monitor and track the metrics over time?

## 　
### Add data profiling to your data reliability strategy
[PipeRider](https://piperider.io/?utm_source=piperiderblog&utm_medium=blog) is an open-source data reliability CLI tool that adds data profiling and assertions to data warehouses such as BigQuery, Snowflake, Redshift and more. Data profile and assertions results are provided in an HTML report each time you run PipeRider.

If you found this article useful please consider liking and [retweeting](https://twitter.com/InfuseAI/status/1582554616092184576?s=20&t=U8_JhQpFZRqjShVTA98vTg)❤.

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">Are you master of your domain, er... pipeline?<br><br>Data pipelines aren&#39;t getting any simpler!<br><br>What kind of monitoring are you running and which metrics are important to you?<a href="https://t.co/EevD4la0bo">https://t.co/EevD4la0bo</a><a href="https://twitter.com/hashtag/dataobservability?src=hash&amp;ref_src=twsrc%5Etfw">#dataobservability</a> <a href="https://twitter.com/hashtag/datamonitoring?src=hash&amp;ref_src=twsrc%5Etfw">#datamonitoring</a></p>&mdash; InfuseAI (@InfuseAI) <a href="https://twitter.com/InfuseAI/status/1582554616092184576?ref_src=twsrc%5Etfw">October 19, 2022</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script> 

