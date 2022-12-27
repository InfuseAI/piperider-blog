---
layout: post
title: "Data reliability testing for dbt state with PipeRider"
subtitle: "PipeRider now supports dbt state for profiling only modified models"
author: PipeRider
background: '/img/posts/06.jpg'
hidedate: true
featured-image: '/img/posts/dbt-state-piperider.jpg'
cta: cta_2.html
---

*tl;dr PipeRider now supports [dbt state](https://docs.getdbt.com/reference/node-selection/methods#the-state-method)! You can profile and run data reliability tests on only the tables that have been modified as part of your dbt state*

<hr />

One of the great features of dbt is [node selection](https://docs.getdbt.com/reference/node-selection/syntax) and the ['state' method](https://docs.getdbt.com/reference/node-selection/methods#the-state-method). Using state, you are able to specify a subset of models (or other resources) to work on. For instance, you might use `state:modified` to only build your dbt models that have changed.

The logic behind state is that **there’s no point rebuilding everything if you’ve only changed part of your project**. Likewise, if you’re using a data quality tool with your dbt project (and you should), then the same logic should apply - **you only want to run your data quality and reliability tests against the modified models**.

The latest version of [PipeRider (0.14)](https://github.com/infuseai/piperider), the open-source data reliability tool, adds exactly this feature. If you’re a dbt user and you’re not using PipeRider, you really should check it out. PipeRider adds profiling and data assertions to a dbt project with zero config.

Here’s a [video](https://www.youtube.com/watch?v=2J2Cu84HonU) that shows it in action, or scroll down for the relevant commands.


{% youtube "https://www.youtube.com/watch?v=2J2Cu84HonU" %}

## Run data profiling and assertions on dbt state

It’s really straightforward to use. Let’s say you’ve modified a dbt model and then built your project specifying only the affected models:

```bash
dbt build --select state:modified+ --state target
```

Now, when you run PipeRider, all you need to do is specify the dbt state using the `--dbt-state` option:

```bash
piperider run --dbt-state target
```

PipeRider will only profile and test models that are included in the specified dbt state, saving you time and computing resources.

## Compare data profiles

PipeRider also has a handy feature to quickly compare data profile reports:

```sql
piperider compare-reports --last
```

You’ll be prompted to select the reports to compare or, if you specify the `--last` option, it’ll automatically compare the last two reports - great! 

Taking it a step further, you can specify to only compare tables that appear either in the base or target report. This ties in nicely to dbt state because you might not want to include all of the unmodified tables in the comparison report.

To specify which report’s tables to limit the comparison to, use the `--tables-from` option. 

```jsx
piperider compare-reports --last --tables-from target-only
```

This command auto compares the last two reports, and only compares tables that appeared in the *target* report. Which, in this case, would be the report that only includes tables modified as per the dbt state.  This is perfect if you want a report that only focuses on the comparison of modified models before-and-after your latest changes.

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">dbt state is a powerful way to build only modified/specified models<br><br>You can now profile and test <a href="https://twitter.com/hashtag/dbt?src=hash&amp;ref_src=twsrc%5Etfw">#dbt</a> states with PipeRider, available now in version 0.14<br><br>👀 Read more<a href="https://t.co/vvV3IMhH2Y">https://t.co/vvV3IMhH2Y</a><br><br>⭐️Star on GitHub<a href="https://t.co/rqp6ynbyeM">https://t.co/rqp6ynbyeM</a><a href="https://twitter.com/hashtag/dataquality?src=hash&amp;ref_src=twsrc%5Etfw">#dataquality</a> <a href="https://twitter.com/hashtag/datareliability?src=hash&amp;ref_src=twsrc%5Etfw">#datareliability</a> <a href="https://twitter.com/hashtag/opensource?src=hash&amp;ref_src=twsrc%5Etfw">#opensource</a> <a href="https://t.co/jk2qvO7uPM">pic.twitter.com/jk2qvO7uPM</a></p>&mdash; InfuseAI (@InfuseAI) <a href="https://twitter.com/InfuseAI/status/1600150571402477569?ref_src=twsrc%5Etfw">December 6, 2022</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script> 


## Get started with PipeRider

As I mentioned above, if you’re a dbt user then PipeRider should be your go-to data reliability tool.  If you already have a dbt project, all you need to do is [initialize PipeRider inside the project](https://docs.piperider.io/cli/dbt-integration) and your data source settings will be automatically detected:

```bash
# inside your dbt project folder
piperider init
```
