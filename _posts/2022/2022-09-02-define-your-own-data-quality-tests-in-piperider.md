---
layout: post
title: "Define your own Data Quality Tests in PipeRider"
subtitle: "PipeRider comes with a built-in suite of data quality assertions, but you can also define your own assertions to meet your needs"
author: PipeRider
background: '/img/posts/06.jpg'
hidedate: true
featured-image: '/img/posts/220902-0.webp'
cta: cta_2.html
---

**tl;dr** [PipeRider](https://piperider.io/?utm_source=piperiderblog&utm_medium=blog) comes with a built-in suite of data quality assertions, but you can also define your own assertions to meet your needs. This guide will show you how to implement a custom assertion to allow a specific number of nulls without raising an alert.

<hr /> 

You don’t always have the luxury of a complete dataset, and that’s not always a bad thing — there are some cases in which a certain amount of missing data, or null values, can be acceptable in a data source.

Sometimes a certain amount of NULL values is OK 

## Missing data? No problem 
Let’s say you have some incomplete data in a sales database and, even so, you still need to perform some calculations based on the data. You might be willing to allow a certain percentage of missing values before worrying about it affecting your results.

[PipeRider](https://piperider.io/?utm_source=piperiderblog&utm_medium=blog) has [built-in assertions](https://docs.piperider.io/cli/data-quality-assertions/assertion-configuration) for testing if a column does not contain nulls, or that a it must be null, but there is no middle-ground for allowing for a certain quantity of nulls — custom assertions to the rescue!

![](/img/posts/220902-1.webp)

*For the rest of this article, I’ll assume you already have a PipeRider project set up — If not, it’s really easy to do, the [Quick Start](https://docs.piperider.io/cli/quick-start) guide will have you up and running in minutes.*

## From data profile to data assertions 
Each time you run PipeRider it creates a [profile of your data](https://docs.piperider.io/data-profile-and-metrics/data-profile), and then by applying data assertions you can test the contents of the profile to ensure the data meets your structural requirements.

Using the missing data example from above, we’ll create a custom assertion that checks the number of nulls in a column, and raises an alert if there are more than our specified amount.

## Custom Column-Assertion Template
Here’s the template we’ll be using to create our custom column-assertion, Steps 1 to 5 in the code-comments are what we’ll be working on:

<script src="https://gist.github.com/DaveFlynn/7f26ee7cdecedef332d4b5601dec721f.js"></script>

## Create your custom column-assertion 
In your PipeRider project, open `.piperider/plugins/customized_assertions.py` in your favorite text editor and paste the above template at the bottom, above where it says `# register new assertions`

Give the assertion a name. Here, I’ve named the class `AssertNullCount` and the name of `assert_null_count`:

```bash
class AssertNullCount(BaseAssertionType):
  def name(self):
    return "assert_null_count"
```

Now, I’ll run you through the commented steps 1 - 5 in the assertion template.

### 1: Get the desired metric
The first thing we need to do is get the value of the desired metric we want to test. For this assertion, we’ll be testing the number of **nulls**.

```
# 1. Get the metric for the desired column, e.g. num of nulls in column
nulls = column_metrics.get('nulls')
```

For a full list of available metrics, check the [Data Profile](https://docs.piperider.io/data-profile-and-metrics/data-profile) page in the PipeRider documentation.

### 2: Get the expected value from the assertion file
You could hard-code the the number of allowed nulls, but then we couldn’t re-use the assertion. Luckily, it’s possible to pass a value from the assertion YAML file into the custom assertion.

Here we grab the value of `allowed_null`s`. I’ll show you how to define the value of this variable in your assertion YAML later on.

```
# 2. Get expectation from assertion file
allowed_nulls = context.asserts.get('allowed_nulls', [])
```

### 3,4: Implement logic to test the metric and either pass or fail
After comparing the value of nulls with the value of allowed_nulls, we return a pass result if nulls is less than or equal to our threshold, and a fail otherwise.

```
# 3. Implement logic to compare expected and actual metric value
if (nulls <= allowed_nulls):
	# 4. return pass (acceptable number of nulls)
	return context.result.success('There are {} null values'.format(nulls))
else:
	# 4. or return fail (more nulls than we expected)
	return context.result.fail(nulls)
```

### 5: Register the new assertion 
Now that you’ve created the assertion, register it with PipeRider. **This goes outside of your new class**, at the bottom of the `customized_assertions.py` file.

```
#register new assertion
register_assertion_function(AssertNullCount)
```

## Completed assertion class
The completed custom assertion class should now look like this: 

<script src="https://gist.github.com/DaveFlynn/37b9f92e2784187566a6b4f8d3101250.js"></script>

## Put your custom assertion into action 
Open the assertions file for the table you want to run the new assertion on. You can find the assertion YAML files in `.piperider/assertions/<table>.yml`. If you generated [recommended assertions](https://docs.piperider.io/cli/quick-start#generate-data-assertions) then your table assertions file should already be populated.

Find the desired column and apply your custom assertion. In example below, I have applied the new assertion to the Global Sales column:

```
Global_sales: # Column Name
  description: 'Combined global sales figures'
  # Test Cases for Column
  tests:
  - name: assert_allowed_nulls
    assert:
        allowed_nulls: 5
```

The last line, `allowed_nulls`, is the value we pass through to the custom assertion and check the actual number of nulls against.

## Run PipeRider to check that it works 
The next time you run PipeRider your custom assertion will be tested.

**Passed assertion**
If it passes, you’ll see the test with the status `[OK]`.

all.Global_sales assertion passed with 5 nulls out of 10 allowed
![all.Global_sales assertion passed with 5 nulls out of 10 allowed](/img/posts/220902-2.webp)

**Failed assertion**
If it fails you’ll see it in the list of **failed assertions**.

all.Global_sales failed with 15 nulls — 5 more than the 10 allowed
![all.Global_sales failed with 15 nulls — 5 more than the 10 allowed](/img/posts/220902-3.webp)

## Take it a step further
Specifying an exact number of allowed nulls might not be an ideal solution for all datasets. For instance, when dealing with large datasets, you might prefer to allow a certain percentage of nulls. In that case, the code we wrote only needs a small adjustment.

All you need to do is get the total number of rows for the table; the number of nulls; then work out the percentage of nulls and test if the percentage exceeds your threshold of allowed nulls.

```
# get total number of rows
total = column_metrics.get('total')

# get the number of nulls
nulls = column_metrics.get('nulls')

#work out the percentage of nulls
percent_nulls = round(((100 / total) * nulls), 2)

# get the number of allowed nulls from your assertion definition
allowed_nulls = context.asserts.get('allowed_nulls')
if (nulls > percent_nulls * allowed_nulls): 
    # too many nulls
    return context.result.fail('{}%'.format(percent_nulls))
else: 
    # acceptable percentage of nulls
    return context.result.success('There are {}% nulls'.format(percent_nulls))
```

You’re only limited by the metrics available in the data profile, and your ability to write Python, so check the [PipeRider documentation](https://docs.piperider.io/) and **start making your data more reliable today**! 

