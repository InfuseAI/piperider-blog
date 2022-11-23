---
layout: post
title: "5 Database Schema Changes Data Engineers Need to Beware Of"
subtitle: "Stay ahead of schema changes and know about issues before they affect downstream"
author: PipeRider
background: '/img/posts/06.jpg'
hidedate: true
featured-image: '/img/posts/database-schema-change.png'
cta: cta_2.html
---

As a data or analytics engineer you need to anticipate the unexpected, especially when building pipelines from data sources that you have no control over. While a data pipeline might be a house of cards, with data observability you’re able to keep an eye on any changes to the underlying structure, and be prepared for schema changes.

Structure is the key point here, as one of the main ways that a data source can change is the schema, or structure, of a database table. The schema is important because the pipelines you build may have specific downstream uses that are directly tied to the current structure of the data. By staying ahead of schema changes you’ll know about potential issues before they affect the data and downstream uses.

As Angela, a data engineer at Sam’s Club, put it in a [recent interview](https://twitter.com/i/spaces/1OwGWwZAZDnGQ?s=20):

> “you never want your end users to actually contact you, (and if they do) you want to be already in the know”

Here are 5 schema changes to look out for, and why you should beware of them:

## 1. Additional columns

Additional columns might seem like one of the more benign changes at first. After all, how could adding some columns to a database affect your pipeline?

### Why you should beware

After a new column is added, there’s no easy way to know if the data was backfilled, without manually checking. That is, for each row, was the data retroactively added? If not, there may be null, zero, or empty values, and you won’t know if they represent valid data or not. This could be problematic if you start using the new column without first knowing the backfill status.

## 2. Column type and attribute changes

Column types are important because they enforce the type of data contained in the column. The way you use the data of a column is based on the expectation that the data is of a certain type. Examples of column type changes include:

- A numeric column changing to string, and vice-versa.
- A numeric type change, such as a decimal changing to an integer.
- Date is a tricky one — is it Date, Datetime, or Timestamp?

### Why you should beware

If you’re expecting a float and get an integer, this could affect the accuracy of any calculations based on the data, especially if you require a certain precision (see column attributes).

Sometimes, column types might not even be enforced, so you might run into problems with mixing types, such as storing text and numbers in the same column. This means you need to be very careful about checking the format of the data.

## 3. Column attributes and constraints

Column attributes refer to the format of the stored data. Things like:

- String length
- Size of an integer
- Decimal precision
- Date format
- Default values
- If NULL values are allowed

### Why you should beware

Changes to numeric types such as integer size, or precision, could affect downstream calculations.

The format of the date could also wreak havoc on your dashboard — is it DD-MM-YYYY, or MM-DD-YYYY? What time zone is this for? These are important questions to ask if you’re building a dashboard that relies on time-specific data.

If the limit on the length of strings changes, it could result in truncated data. An issue that might go unnoticed if not manually checked for.

## 4. Column renaming

Renaming a column is a big change. If tables are being used in production you’d hope to be notified of a change such as this, but with third party data sources that might not happen. This one could really get you if you’re not paying attention.

### Why you should beware

Your transformations and data modeling queries rely heavily on column naming. One column name-change could result in a broken pipeline causing data to stop flowing downstream.

## 5. Column misuse

Column misuse is more of a data quality issue than a schema change but, like a schema change, could cause issues for you when using the data. When a column is repurposed, it’s used for a purpose it wasn’t originally intended for. If there’s no data dictionary, or documentation is not kept up-to-date, then you could easily be caught out by this one.

### Why you should beware

One example of column misuse is putting additional data into a column, instead of creating another column. For instance, a product sales table might start including product attributes, such as size and color, in the description column, instead of creating new columns for the attributes.

The meaning of a column might also change over time and, instead of adjusting the database accordingly, an existing column is ‘repurposed’ for use. Without you knowing, the column now includes completely different data than what you expect.

## How to avoid being caught out

As mentioned in the introduction, it’s all a matter of having the knowledge that a change has taken place — As the saying goes “[knowledge is power, France is bacon](https://knowyourmeme.com/memes/france-is-bacon)”. If you know a change has taken place, you can react and make sure that data pipeline continues to work, before downstream issues occur.

For data teams, that knowledge comes from [data monitoring and observability](https://blog.infuseai.io/data-monitoring-be-the-master-of-your-pipeline-ba464b66888). With proper data observability in place you can know the current structure of the database, and how that compares to previous states.

Highlighting that schema changes have taken place, along with other data changes, is one of the things [we're working on](https://blog.infuseai.io/how-to-be-more-confident-making-data-model-changes-76a2f65feffa) with [PipeRider](https://github.com/infuseai/piperider).

## Your experiences

Have you been bitten by schema change? Let me know what happened and how you discovered the change.

If I missed any important or obvious schema changes to look out for, please tell me and I’ll improve the list.

