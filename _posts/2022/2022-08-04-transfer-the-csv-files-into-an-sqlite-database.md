---
layout: post
title: "Transfer the CSV Files into an SQLite Database"
subtitle: "Use open-source tool csvs-to-sqlite to convert CSV files into SQLite databases"
author: PipeRider
background: '/img/posts/06.jpg'
hidedate: true
featured-image: '/img/posts/220804-0.png'
cta: cta_2.html
---

Datasets are readily available as CSV files on websites such as Kaggle and other real-world datasets. However, CSV isn’t really suitable for querying and transforming easily. Therefore, it’s better to store the data in a database.

In this article, you will use csvs-to-sqlite to convert CSV files into SQLite databases. Once the data is in a database, it’s easier for users to query with SQL and add to their ETL service.

We have to get the dataset first, here is an example of the [CPBL dataset](https://github.com/ldkrsi/cpbl-opendata).

<hr />

## Convert CSV to SQLite

"[csvs-to-sqlite](https://github.com/simonw/csvs-to-sqlite)" tool is an open-source project and put it in the Github. We can easily use the pip install method to install the tools.

You can use the following commands to download the data and install the [python package](https://pypi.org/project/csvs-to-sqlite/).

<script src="https://gist.github.com/LiuYuWei/a9ec256303f6c63b5958a4b12d03e625.js"></script>

After configuring the environment, we can convert the CSV files into several SQLite databases.

The format of the csvs-to-sqlite command is:
```
csvs-to-sqlite /path/to/your.csv sqlite-db-name.db
```
<script src="https://gist.github.com/LiuYuWei/e4cad03c0bee591b6105bc1056a22f0b.js"></script>

The result after we convert the CSV files into a database:
![The result after we convert the CSV files into a database](/img/posts/220804-1.webp)

## Verify the CSV was imported correctly
We can now check if the data was successfully inserted into the SQLite database using the “sqlite3” command line tool to open the database and query the data.

<script src="https://gist.github.com/LiuYuWei/29cd132ca02351bb3f66a1680c521d39.js"></script> 

We have successfully queried the SQLite data, which is the same as the CSV data. Now, If a data engineer wanted to query the historical data of an individual baseball player, they could use SQL to query the data faster.

The result of querying data from the SQLite database:
![The result of querying data from the SQLite database](/img/posts/220804-2.webp)



---
### I am Simon
Hi, I am Simon, Customer Success Engineer in InfuseAI. If you think the article is helpful to you, please give me applause. Welcome to provide some suggestions and discuss with me in InfuseAI [Discord](https://discord.gg/xKxsdPx4d5).
Linkedin: [https://www.linkedin.com/in/simonliuyuwei/](https://www.linkedin.com/in/simonliuyuwei/)

