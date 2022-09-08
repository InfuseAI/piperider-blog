---
layout: post
title: "Define your own Data Quality Tests in PipeRider"
subtitle: "Problems look mighty small from 150 miles up"
author: Dave Flynn
date: 2022-09-06 15:25:00 +0800
background: '/img/posts/06.jpg'
featured-image: '/img/posts/custom-assertions.png'
---

After you’ve transformed the data in your data warehouse and sent it on its way, you might think that your job is done. That is, until you get a call that there’s missing data, an unexpected schema change, or some data drift or outlier has been introduced. To understand when these issues might have occurred, you need some form of data observability in your pipeline.

Data observability means that you can monitor the data moving through the pipeline, be alerted to any changes or issues with the data structure, and compare data to help visualize change and aid in tracking down issues.

With the open-source data observability toolkit, PipeRider, you can add data observability to your data source and start understanding more about your data in minutes with:

- Non-intrusive implementation - Focus on understanding your data, not changing it
- Data profiling - In-depth analysis of the structure of your data source
- Data assertions - Ensure your data stays within acceptable ranges through testing
- HTML report - The data profile and testing results are exported to an HTML report

## 1. Install PipeRider

PipeRider is installed via pip:

```python
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

```python
pip install -U 'piperider[postgres,snowflake]'
```

{% youtube "https://www.youtube.com/watch?v=vZVHo09fD-c" %}

<p>You don’t always have the luxury of a complete dataset, and that’s not always a bad thing — there are some cases in which a certain amount of missing data, or null values, can be acceptable in a data source.</p>

<h2>Missing data? No problem</h2>

<p>Let's say you have some incomplete data in a sales database and, even so, you still need to perform some calculations based on the data. You might be willing to allow a certain percentage of missing values before worrying about it affecting your results.</p>

<p>PipeRider has built-in assertions for testing if a column does not contain nulls, or that a it must be null, but there is no middle-ground for allowing for a certain quantity of nulls — custom assertions to the rescue!</p>

<p>Here's a code test:</p>

You can write regular [markdown](http://markdowntutorial.com/) here and Jekyll will automatically convert it to a nice webpage.  I strongly encourage you to [take 5 minutes to learn how to write in markdown](http://markdowntutorial.com/) - it'll teach you how to transform regular text into bold/italics/headings/tables/etc.

**Here is some bold text**

## Here is a secondary heading

Here's a useless table:


<table class="table">
  <thead>
    <tr>
      <th scope="col">Number</th>
      <th scope="col">Next number</th>
      <th scope="col">Previous number </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">1</th>
      <td>Five</td>
      <td>Six</td>
      <td>Four</td>
    </tr>
    <tr>
      <th scope="row">2</th>
      <td>Ten</td>
      <td>Eleven</td>
      <td>Nine</td>
    </tr>
    <tr>
      <th scope="row">3</th>
      <td>Seven</td>
      <td>Eight</td>
      <td>Six</td>
    </tr>
  </tbody>
</table>

![foo](/img/posts/06.jpg)



How about a yummy crepe?

![Crepe](https://s3-media3.fl.yelpcdn.com/bphoto/cQ1Yoa75m2yUFFbY2xwuqw/348s.jpg)

It can also be centered!

![Crepe](https://s3-media3.fl.yelpcdn.com/bphoto/cQ1Yoa75m2yUFFbY2xwuqw/348s.jpg){: .mx-auto .d-block :}

Here's a code chunk:

~~~
var foo = function(x) {
  return(x + 5);
}
foo(3)
~~~

And here is the same code with syntax highlighting:

```javascript
var foo = function(x) {
  return(x + 5);
}
foo(3)
```

And here is the same code yet again but with line numbers:

{% highlight javascript linenos %}
var foo = function(x) {
  return(x + 5);
}
foo(3)
{% endhighlight %}

## Boxes
You can add notification, warning and error boxes like this:

### Notification

{: .alert .alert-primary}
**Note:** This is a primary alert box.

### Warning

{: .alert .alert-warning}
**Warning:** This is a warning box.

### Error

{: .alert .alert-danger}
**Error:** This is an error box.


