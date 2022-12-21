---
layout: post
title: "5 Metrics Elon Musk Should Check In Twitter’s Data"
subtitle: "If Musk actually gets his hands on this data, what kind of things might he be looking for?"
author: PipeRider
background: '/img/posts/06.jpg'
hidedate: true
featured-image: '/img/posts/221013-0.webp'
cta: cta_2.html
---

The value of Twitter has been [in the news](https://www.theverge.com/2022/10/4/23387592/elon-musk-twitter-deal-lawsuit-faq) a lot recently. Antics related to Elon Musk’s possible Twitter buyout has led to a legal battle that may result in Twitter releasing a snapshot of data on its users and tweets. If Musk actually gets his hands on this data, what kind of things might he be looking for?

<hr /> 

Data profiling is a great way to analyze and explore a dataset. A data profile not only helps you to understand the structure of a dataset, but the statistical metrics are also great for exploratory analysis.

In this article, I take some publicly available Twitter datasets and run them through a [data profiler](https://piperider.io/?utm_source=piperiderblog&utm_medium=blog) to see what interesting metrics I can find.

## 　
## The datasets
I used two datasets for this analysis:

* A portion of the [Archive Team Twitter Stream](https://archive.org/details/archiveteam-twitter-stream-2021-06) dataset from June 2021. This dataset comes in JSON form, so you’ll need to use a tool such as [twitter_to_csv](https://github.com/cantino/twitter_to_csv) to convert the raw Twitter API JSON to CSV.
* A pre-prepared dataset from Kaggle. I found the Gender classification set, with data from 2015, was the most useful as it retained much of the user data, such as profile image URL, retweet count, and profile description.

For both methods I used [PipeRider](https://piperider.io/?utm_source=piperiderblog&utm_medium=blog), an open-source CLI tool for profiling datasets. It outputs an HTML report which makes it easy to see the metrics. There are also data assertions if you need to add testing to your dataset.

## 　
## The metrics
So, what things might Elon Musk, or anyone analyzing the value of a social network data need to look out for? What interesting metrics can be found, and what are the implications in regard to determining the ‘value’ of Twitter users and Tweets.

## 　
### 1. Account creation date
Looking at the account created date in the gender dataset, there are active accounts that date back all the way to 2006.

**Implication** 

Twitter has good user retention, as these are users that have been coming back for years.

Twitter account creation date metric via PipeRider: 
![](/img/posts/221013-1.webp)

## 　
### 2. Profile image
You might not think that a profile image could indicate much, but the notorious [Twitter egg](https://www.vox.com/2017/3/31/15139192/twitter-egg-profile-default-change) fiasco proves otherwise. 18.3% of profile images in the Kaggle dataset are duplicates, and it looks like this is because they are using the default image.

The Archive Team dataset was around the same, at 17.1% for my sampling.

Twitter profile image metrics via PipeRider:
![](/img/posts/221013-2.webp)


**Implication**

This could be an indication of throw-away accounts, bots, trolls, or generally users who aren’t invested enough to update their profile image.

## 　
### 3. Duplicated Tweet content
This doesn’t refer to retweets, or quote tweets, but to tweets with identical content. Why would a tweet contain the same content? There was 8.7% of tweets with duplicated content in the Kaggle dataset.

**Implication**

This could be an indication of a bot farm spreading propaganda, or users could simply be clicking the “share this article” button on news websites.

Twitter metrics indicate possible bot messages via PipeRider: 
![](/img/posts/221013-3.webp)

The Kaggle dataset shows a lot bizarre of Weather Chanel tweets.

Interestingly, these tweets cannot be found by searching Twitter now. All I can find is [someone asking](https://twitter.com/ArdentCrayon/status/722136691809525764?s=20&t=9IY8SlHv4k813B-xxwjGxw) why there are so many bots spamming the weather channel.

The Archive Team dataset shows many retweets of an account for a Korean band (I think). The [account](https://twitter.com/WeareoneEXO) has 13million followers, so I suppose a few thousand fans retweeting isn’t out of the ordinary.

Tweet content metrics via PipeRider:
![](/img/posts/221013-4.webp)

## 　
### 4. Retweet count
Retweet count was extremely low in both datasets — 99.9% of the tweets in the Kaggle set were not retweeted.

**Implication**

It could mean low interaction rates on Twitter, but is probably just an indication that the dataset time frame is too narrow — only an hour, and that it takes a while for a tweet to gain momentum. This could be one to analyze over a period of a few hours or days.

Retweet metrics via PipeRider:
![](/img/posts/221013-5.webp)

## 　
### 5. Follower count
Follower count not only indicates how popular you are, but also if users are interacting and ‘listening’ to each other on Twitter. Are most users shouting into the wind? According to the Archive Team dataset, 4800 users were talking to themselves during that time frame.

**Implication**

It’s difficult to gauge this one without more analysis of the accounts with zero followers. They could be the bots we mentioned earlier, or just angry loners shouting in the wind.

Follower count metrics via PipeRider: 
![](/img/posts/221013-6.webp)

## 　
## Conclusion
Data exploration is fun, even if you’re not a billionaire mulling over the potential purchase of a $44 billion social network.

Data profiling can provide interesting insights into a dataset that you may not have previously thought of. Even the process of cleaning and transforming data in preparation for analysis can yield interesting results. For instance, while importing the Archive Team dataset, I found that there were many ‘deleted’ entries listed. I presume these are deleted tweets, a figure that could also offer some valuable insight.

## 　
## Add data profiling to your data reliability strategy
If you’re interested in the tool I used here, check out PipeRider — it’s a CLI tool that profiles all the popular data warehouses and provides an HTML data profile report.

Also, before you finish the reading the contracts for your Twitter purchase, please follow us on Twitter — we’re [@infuseai](https://twitter.com/infuseai) ❤

If you found this article interesting please [retweet](https://twitter.com/InfuseAI/status/1580574430442377217?s=20&t=GwuHVBwmjPMAU8nWlXetBw) to support more content like this.

