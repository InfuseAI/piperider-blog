---
layout: post
title: "How do you know you can trust your data?"
subtitle: "Trustworthy data: the foundation of data-driven decision making"
author: PipeRider
background: '/img/posts/06.jpg'
hidedate: true
featured-image: '/img/posts/221023-0.webp'
cta: cta_2.html
---

Every decision in business is made based on supporting data. “Data-driven” is more than just a buzzword for meetings, it’s a way for a company to be self-aware. Using metrics derived from all sorts of data, it’s possible to understand the performance of each operational unit in a business. From sales figures to marketing efforts, from time sheets to billable hours, data helps us determine what is the correct decision to make, backed up by proof in the form of metrics.

With data being such a valuable commodity, there has to be trust in it. By the time data makes its way downstream, it could have undergone many transformations on the way. With each ingestion, transformation, or abstraction, there is the possibility of mistakes being introduced into the data pipeline.

At each step of the way along the pipeline, how do you ensure that the data is correct and can be trusted?

![](/img/posts/221023-1.webp)
*If you can’t trust your data, you can’t make data-drive decisions.*

## 　
## Can we put that in writing?
Recently, [data contracts](https://dataproducts.substack.com/p/the-rise-of-data-contracts) have been hailed as the savior of the relationship between data producer and data consumer. Data contracts define the ‘rules of the game’ by explicitly stating things like schema structure, ingestion frequency, source tables, and even contact information for stakeholders.

By clearly [defining the requirements of the the data](https://davidsj.substack.com/p/yet-another-post-on-data-contracts#%C2%A7what-a-data-contract-should-contain), the data producer knows what data to serve, and in what format, and the data consumer knows what they will be receiving.

Once the scale of your data pipeline reaches a certain threshold, and you’re [collecting metrics *about* the pipeline](https://blog.piperider.io/data-monitoring-be-the-master-of-your-pipeline.html), then it might be time to introduce data contracts. As Gleb, of Data Fold, [puts it](https://www.datafold.com/blog/the-best-data-contract-is-the-pull-request), when “metadata becomes big data… when something breaks, figuring out what the origin is becomes a huge task”. If you’re clear about what’s happening between the connections in the pipeline, this task is made a whole lot easier.

## 　
## Quality data? Prove it!

If you don’t have the luxury of implementing a new system such as data contracts, there are still other things you can do to ensure data quality, and subsequently data trust. Through data profiling and data assertions you’re able to ensure that the data continually meets your requirements.

Data assertions are data ‘contracts’ on some level. Assertions enable you to verify the structure and contents of the data source. If a data assertion fails then you know that some predetermined requirement of the data has not been met. If the the data assertions pass then this is proof that the data meets the needs for downstream use.

Actual proof could take the form of a [data profile](https://docs.piperider.io/data-profile-and-metrics/data-profile) that shows a breakdown of metrics about the data, or even better, a set of [data assertions](https://docs.piperider.io/cli/data-quality-assertions) and results that prove the data is fit for purpose. By generating profiling reports regularly and automating assertions after ingestions or transformations, you can be sure that unexpected errors are not introduced and the pipeline is functioning correctly.

## 　
## The path to data trust
The path to trust in a data pipeline comes from confidence that the data is complete. In turn, confidence in that data comes from proving that the data meets the needs of the data consumer, either enforced through data contracts, or demonstrated with assertion test results.

Without some form of proof of data quality, or method to determine that data is not changing in a way that might break downstream usage, there’s no real way to trust that data is accurate.

What methods are you using to test data after ingestions or transformations?

Are you using data contracts, either in production or testing?

I’d love to hear about your use-cases and experiences — please leave a comment and share your experience.


## 　
### Add data profiling to your data reliability strategy
[PipeRider](https://piperider.io/?utm_source=piperiderblog&utm_medium=blog) is an open-source data reliability CLI tool that adds data profiling and assertions to data warehouses such as BigQuery, Snowflake, Redshift and more. Data profile and assertions results are provided in an HTML report each time you run PipeRider.



