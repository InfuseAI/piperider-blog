---
layout: post
title: "PipeRider data profiling just got more colorful (and useful)"
subtitle: "PipeRider 0.5.0 was released last week and introduces some CLI updates"
author: PipeRider
background: '/img/posts/06.jpg'
hidedate: true
featured-image: '/img/posts/220802-0.png'
cta: cta_2.html
---

[PipeRider 0.5.0](https://github.com/InfuseAI/piperider/releases/tag/v0.5.0) was released last week and introduces some CLI updates that improve visual feedback during profiling, and the reporting feature adds some options to make it more suitable for use in your CI pipeline.

*In case you missed it — [PipeRider](https://piperider.io/?utm_source=piperiderblog&utm_medium=blog) is a new open-source [data reliability](https://blog.piperider.io/test-your-data-quality-in-minutes-with-piperider.html) tool with data profiling, data assertions, and support for [popular data sources](https://blog.piperider.io/add-data-profiling-and-assertions-to-dbt-with-piperider.html).*

<hr />

## CLI now with extra prettiness
The PipeRider CLI is now includes extra visual feedback when profiling in the form of per-table progress bars.

### Progress bars — so satisfying
The progress bars show how many tables are left to profile, the number of columns that are being profiled, and a timer.

![Progress bars — satisfying :)](/img/posts/220802-1.gif)

This enables you to see where you are in the profiling progress — no more thinking that the profiler hung when profiling your beefy dbt models.

### Tabular Summary
The profiling and data assertions summary is now displayed in a table so you can see test results at a glance.

![Profiling and data assertion test results are now tabular — awesome!
](/img/posts/220802-2.webp)

Extra color has also been sprinkled around to make the CLI output generally easier to read. So now it’ll fit better with your colorful terminal theme ([Dracula](https://draculatheme.com/terminal), anyone?).

If you’re working on the command line all day, then these should be some welcome additions.

## Reports where you want them, when you want them
For reporting, we’ve got a some great features to make generating and exporting reports more convenient.

### Output Location
The default location for reports is `.piperider/outputs`, but this isn’t always the best location, especially if you want to share the reports with BI or other users who don’t want to dig around in a hidden folder.

In PipeRider v0.5.0 you can choose the output location for a report by using the `-o` option and specifying a location, e.g.

```
piperider generate-report -o ~/piperider-reports
```

This works for `piperider run` and `piperider compare-reports`, too!

## Compare the last two reports automatically
On the subject of comparing reports, now you can compare the last two reports without having to select them manually — Just use the `--last` option:

```
piperider compare-reports --last
```

Pair this with a custom output location and you can easily automate PipeRider reports as part of your CI pipeline — we’ll have a tutorial/show-case on how to do this very soon. Make sure to follow us to be notified.

Check out the documentation [command reference](https://docs.piperider.io/cli/piperider-cli) for more info, there are also a couple of how-to docs for [generating](https://docs.piperider.io/cli/quick-start#run-piperider-profile-data-and-generate-report) and [comparing](https://docs.piperider.io/cli/quick-start#run-piperider-profile-data-test-assertions-generate-report) reports.

---

