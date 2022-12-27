---
layout: post
title: "Spotlight on Data Reliability"
subtitle: "Open-Source Spotlight welcomed us back to to demo PipeRider"
author: PipeRider
background: '/img/posts/06.jpg'
hidedate: true
featured-image: '/img/posts/220823-0.webp'
cta: 
---

**tl;dr** Open-Source Spotlight welcomed us back to to demo [PipeRider](https://piperider.io/?utm_source=piperiderblog&utm_medium=blog), the open-source data reliability toolkit. In the video, CL Kao, InfuseAI’s CEO, shows how it’s possible to profile and test a data set, and then generate a visualization report with just a few commands.
<hr />

Data quality has a new hero!

We’ve been on Open-Source Spotlight a [few](https://www.youtube.com/watch?v=Q3aMaxBH1-o) [times](https://www.youtube.com/watch?v=2ebo1H0XgEs) [already](https://www.youtube.com/watch?v=akhj7or9gmQ), and this time CL Kao, the CEO of InfuseAI, was invited to demonstrate [PipeRider](https://piperider.io/?utm_source=piperiderblog&utm_medium=blog).

PipeRider is your open-source data reliability toolkit for adding data profiling and data quality assertions with visualization reports to your data warehouse.

## Break it down
That’s quite a mouthful of features, so let’s break down what PipeRider can do (I’ve linked to the relevant documentation pages): 

* Data profiling: PipeRider will profile your data source, providing insightful metrics about the structure of your data.
* Data Assertions: Use PipeRider’s built-in data assertion suite to test the structure and contents of your data profile. You’ll be alerted when your data assertions fail.
* Visualization Report: From the data profile, PipeRider will create an HTML report that shows the structure of your data source, including test results.
* Report Comparison: Compare past data profiling reports to see how your data source has changed between runs.
* Supported Data Warehouses: SQLite, Postgres, Snowflake, and dbt are supported (PipeRider v0.6), with BigQuery and Redshift support just days away (PipeRider v0.7). And you can find more data source on [Supported Data Sources documentation](https://docs.piperider.io/cli/supported-data-sources).

## Watch the demo 

Watch the video to see PipeRider in action: 

{% youtube "https://www.youtube.com/watch?v=03MyOkIo8Hg" %}

*[Open Source Spotlight](https://www.youtube.com/playlist?list=PL3MmuxUbc_hJ5t5nnjzC0F2zan76Dpsz0), the video series by the [DataTalks.club](http://datatalks.club/) community continues to give back to the open-source community by providing a platform for projects to demo what they’re working on. Definitely check out the [YouTube channel](https://www.youtube.com/datatalksclub) if you’re involved in data and/or machine learning.*

## How to get started with data reliability
PipeRider is available now. It’s open-source, free to use, and well documented. As of writing, PipeRider is about to release version 0.7. The version demoed in the video above is 0.3, so make sure to check the websites below for up-to-date information:

* [Official PipeRider website](https://piperider.io/?utm_source=piperiderblog&utm_medium=blog)
* [GitHub Repo](https://github.com/InfuseAI/piperider)
* [Documentation](https://docs.piperider.io/)

## We need your feedback
After you’ve used PipeRider, tell us what you think. Good or bad, we want to know. Get in touch in one of the following ways:

* Twitter[@infuseai](https://twitter.com/infuseai)
* [Discord Community](https://discord.gg/xKxsdPx4d5)
* [GitHub Issue](https://github.com/InfuseAI/piperider/issues)
* Mastodon [@piperider@fosstondon.org](https://fosstodon.org/@piperider)