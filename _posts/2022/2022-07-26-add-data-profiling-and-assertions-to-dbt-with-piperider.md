---
layout: post
title: "Add Data Profiling and Assertions to dbt with PipeRider"
subtitle: "Data profiling helps you understand your data."
author: PipeRider
background: '/img/posts/06.jpg'
hidedate: true
featured-image: '/img/posts/220726-1.png'
cta: 
---


### tl;dr

Data profiling helps you understand your data. When used with data assertions, a data profile can be used to determine data reliability. PipeRider is a non-intrusive open-source platform for adding profiling and assertions to data sources (such as dbt, Postgres, Snowflake). Star PipeRider on [Github](https://github.com/InfuseAI/piperider).

![PipeRider generates an HTML report with assertion results](/img/posts/220726-1.png "PipeRider generates an HTML report with assertion results")

### Data profile

Profiling is super important for understanding your data. A data profile is essentially data *about* your data. On its own a data profile can provide interesting insights about the data, but the real value comes from pairing the profile with data assertions. Together they form the basis of data reliability. Through data assertions you can define the acceptable norms for your data, and then test that your profile meets this specification.

### \[data]Pipe\[line]Rider

With PipeRider you can easily add data profiling and assertions to your dbt project* and start profiling and testing your dbt models.

PipeRider shows profiling results on the command line, and also in an HTML report. Plus, if you run your dbt tests as part of the PipeRider run, they'll also be included in the report.

*PipeRider also works with other data sources, such as Snowflake, Postgres, SQLite, but for this tutorial I'll focus on dbt.*

If you'd prefer to watch how this is done then check out the [YouTube video](https://www.youtube.com/watch?v=dnUq35s8AoY). Otherwise read on.

### dbt, yeah you know me

This guide assumes that you already have a dbt project ready to go, and that your dbt project is using either Snowflake or Postgres as a data source. Let's add data reliability to your dbt project:

### Install PipeRider

Install PipeRider using pip and specifying the data source your dbt project uses. I recommend using a virtual environment such as `venv` or `Conda` .

**Postgres**

```pip install 'piperider[postgres]'```

**Snowflake**

```pip install 'piperider[snowflake]'```

(don't forget the quotes)

### Initialize PipeRider

Inside your dbt project, run the following command to initialize PipeRider:

```piperider init```

![PipeRider init automatically detects your dbt project](/img/posts/220726-2.png "PipeRider init automatically detects your dbt project")

PipeRider will then automatically detect your dbt data source settings from your `dbt_project.yml` and `profiles.yml`.

### Check your connection

To test the connection to your data source, run the diagnose command:

```piperider diagnose```

In the Check Connections section, you should see your dbt models listed.

![Check that PipeRider can connect to your data source](/img/posts/220726-3.png "Check that PipeRider can connect to your data source")


### Run PipeRider

Now all you need to do is run PipeRider!

```piperider run```

Since this is a dbt project, you likely already have some dbt tests configured. If you want your dbt tests to appear on your PipeRider report you can add the `--dbt-test` or `--dbt-build` option to the command. Check the [PipeRider docs](https://docs.piperider.io/piperider-cli) for more info on available options.

### Profile and Assertions

PipeRider will profile the tables and columns from your data source and, as this is the first run, prompt to generate some recommended assertion files.

![Data profiled, do you ant to generate recommended assertions?](/img/posts/220726-4.png "Data profiled, do you ant to generate recommended assertions?")

If you choose '**yes**', PipeRider will make assertion files with some sensible defaults based on the current structure of your data.

If you choose '**no**', then PipeRider will create skeleton assertion files.

Choose 'yes' and you'll see that PipeRider creates assertion files for your tables, and then tests them against the recommended assertions.

![PipeRider tests the data source against the assertions](/img/posts/220726-5.png "PipeRider tests the data source against the assertions")


As it's the first run, and you're using recommended assertions, all of the assertions pass. You'll find out how to edit the assertions below.

### HTML Report

At the end of the CLI output, you'll also find a link to the PipeRider report.

![PipeRider run summary and link to the generated HTML report](/img/posts/220726-6.png "PipeRider run summary and link to the generated HTML report")

The report contains the data profile for each table, plus the PipeRider assertion and dbt test results (if you ran those as well).

![A sample of PipeRider's data profile report](/img/posts/220726-7.png "A sample of PipeRider's data profile report")


### Assertions

The recommended assertions provide some sensible defaults that you can use as a starting off point. If you're confident your data is currently in good health, then you can leave them as-is.

Most likely, you'll want to review the data profile in your PipeRider report, and then adjust the recommended assertions as you see fit.

The assertion files for your tables can be found in `.piperider/assertions`

![Assertions files can be found in .piperider/assertions](/img/posts/220726-8.png "Assertions files can be found in .piperider/assertions")

Open one of the assertion files and you'll see the defaults that PipeRider has set up for you.

![An example of a PipeRider recommended assertions file](/img/posts/220726-9.png "An example of a PipeRider recommended assertions file")

  
PipeRider comes with some [built-in assertions](https://docs.piperider.io/data-quality-assertions/assertion-configuration) you can use to test your data profile. If you want to get your hands dirty then you can also make [custom assertions](https://docs.piperider.io/data-quality-assertions/custom-assertions) --- if it's in your data profile, you can test it.

After updating your assertion files, simply run PipeRider again to test your data profile against the new assertions. Failed assertion results can be viewed both on the CLI, and in the generated reports.

![PipeRider CLI output with failed assertion](/img/posts/220726-10.png "PipeRider CLI output with failed assertion")


### What's next?


There's lots more to check out with PipeRider, such as [comparing reports](https://docs.piperider.io/how-to/compare-reports), regenerating assertions, and [GitHub actions](https://docs.piperider.io/how-to/github-action). Check out the [PipeRider documentation](https://docs.piperider.io/) for full details of all features.

### InfuseAI is making data reliability tools

We're InfuseAI: lovers of open-source, data-quality aficionados.

Tell us you want better data reliability by:

-   Staring PipeRider on [Github](https://github.com/InfuseAI/piperider)
-   Joining the InfuseAI [Discord community](https://discord.gg/328QcXnkKD)
-   Saying hi to [@infuseai](https://twitter.com/InfuseAI) on Twitter
-   Clapping or giving us some feedback in the comments 

### If you read here, you might want to learn more about data reliability: 
* [Data Reliability Automated with PipeRider](https://blog.piperider.io/data-reliability-automated-with-piperider.html)
* [Guide to Data Reliability](https://blog.piperider.io/guide-to-data-reliability.html)
