---
layout: post
title: "How to Use PipeRider's Built-in Assertion and Custom Assertion to Test the Water Quality Kaggle Dataset"
subtitle: "Use PipeRider's assertion method to test the water quality kaggle data"
author: PipeRider
background: '/img/posts/06.jpg'
hidedate: true
featured-image: '/img/posts/220727-0.png'
cta: cta_2.html
---

*tl;dr PipeRider can help detect data issues in a water quality dataset through data profiling and custom assertions, which can be useful for determining the drinkability of water and solving problems immediately if alerts are raised.*

<hr />

Determining the drinkability of water is the perfect case for a data reliability tool. Not only can we detect if there is missing data, but also when values fall outside of safe ranges. If the water resources management center has a good data assertion tool to detect the water quality, they can solve the problem immediately. Also, the manager and the employee can see a daily report to know the data distribution and water status. If PipeRider’s data assertions raise an alert, they can make a decision and better manage it.”

In this article, I will use a Kaggle water quality dataset and show how PipeRider can help detect data issues through data profiling and custom assertions.

[PipeRider](https://piperider.io/?utm_source=piperiderblog&utm_medium=blog) is a data quality toolkit for data professionals. With PipeRider, you can profile your data sources, create highly customizable data quality assertions, and generate insightful reports.

## Get the dataset from Kaggle

First, the Kaggle website stores the [water quality](https://www.kaggle.com/datasets/adityakadiwal/water-potability) dataset. We need to download it and put it into the environment. 


If you want to use the Kaggle CLI tool, you need to download the Kaggle key JSON file from the Kaggle website. The Proceed as follows:

Go to "Account", go down the page, and find the "API" section.
Click the "Create New API Token" button.
We will download the "kaggle.json" file.
Put the file into `~/.kaggle/` folder.

![Download the API token JSON file on the Kaggle Account page.](/img/posts/220727-1.webp)

Then, we can download the datasets through the Kaggle CLI tool.

```bash
pip install kaggle

kaggle datasets download -d adityakadiwal/water-potability

unzip water-potability.zip
```

## Transfer CSV to SQLite
PipeRider supports four data sources: dbt integration, Postgres Connector, Snowflake Connector, and SQLite database. Here we use SQLite as our database example.

However, we need to transfer the CSV file into the SQLite database for PipeRider’s suitable database. Here, We can use the open source tool [csv-to-sqlite](https://github.com/simonw/csvs-to-sqlite) to transfer the CSV files to the SQLite database.

You might also want to check the article of [Transfer the CSV Files into an SQLite Database](https://blog.piperider.io/transfer-the-csv-files-into-an-sqlite-database)

Follow the command line to transfer the CSV files to the SQLite database.

```bash
pip install csvs-to-sqlite
csvs-to-sqlite water-potability.csv water-potability.db
```

## Add build-in assertion
Now, we can start to use PipeRider. We provide a Quick Start tutorial on the documentation page to show how to use PipeRider. You can follow the method to initialize, configure, diagnose and run PipeRider. After you run the `piperider run` command, you will get the “.piperider” folder in your project folder.

![The structure of the .piperider folder](/img/posts/220727-2.webp)

Although PipeRider provides an automatic assertion generation method, we want to configure our logic assertion. For example, the range of PH values is 0 to 14. If the value is over the content of values, then the data detection has some problem, and the users need to collect the data again. PipeRider provides two types of built-in assertions, one takes no parameter, and the other takes parameters.

[Built-In Assertions Guide](https://docs.piperider.io/cli/data-quality-assertions/assertion-configuration)

You can go to `.piperider/assertions/` to add assertions in `<table>.yml`. Here is an example of the built-in assertion yaml file.

<script src="https://gist.github.com/LiuYuWei/27dd7c6ec5685f13de9810accb9a3f6a.js"></script>

After modifying the YAML file, rerun the `piperider run` and see the assertion result.

![The result of piperider run (We configure the built-in assertion YAML file.)](/img/posts/220727-3.webp)

## Add custom assertion

We can see that some assertions failed because the maximum value range exceeded the WHO recommended value. If the user views the assertion error. The user needs to find the root cause of the datasets and improve the water quality.

In the description in the Kaggle datasets, we can see the content that tells us, “WHO has recommended maximum permissible limit of pH from 6.5 to 8.5.” Therefore, I want to test that the average value is in the range of 6.5 and 8.5. However, the built-in assertion method does not have this method. We need to write our own logic assertion to do the testing.

PipeRider provides a few built-in assertions and supports custom assertions as *plugins* that can satisfy your data quality check requirements. In this showcase, we add the new *assert_column_avg_in_range* assertion method and use the assertion to test the data profiling values.

PipeRider, by default, will load python files under `.piperider/plugins` custom assertion functions automatically. `.piperider/plugins` is created `piperider init` with a scaffolding of a custom assertion function, `customized_assertions.py`. You can rename the file or generate assertion functions in other python files.

<script src="https://gist.github.com/LiuYuWei/d7168d5cda4b6296997cc489be3d5687.js"></script>

After modifying the YAML file, rerun the `piperider run` and see the assertion result.

![The result of piperider run (We add the custom assertion method.)](/img/posts/220727-4.webp)

The result shows that the new assertion method is successfully tested. You can follow the python class structure to try the specific assertion method.

Also, You can check the history assertion result in Pipeider UI.

![Assertion testing in PipeRider UI](/img/posts/220727-5.webp)

---

### I am Simon
Hi, I am Simon, Customer Success Engineer in InfuseAI. Please give me applause and also welcome to provide me with some suggestions if you think the article is helpful for you. Welcome to discuss with me in InfuseAI [Discord](https://discord.gg/xKxsdPx4d5).  
Linkedin: [https://www.linkedin.com/in/simonliuyuwei/](https://www.linkedin.com/in/simonliuyuwei/)

