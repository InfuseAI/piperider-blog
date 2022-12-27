---
layout: post
title: "Share the Spectacular World Cup construction with ChatGPT"
subtitle: "See how ChatGPT introduces Lusail city in visualization"
author: PipeRider
background: '/img/posts/06.jpg'
hidedate: true
featured-image: '/img/posts/221215-chatgpt-0.jpg'
cta: cta_2.html
---

The [World Cup](https://www.fifa.com/fifaplus/en/tournaments/mens/worldcup/qatar2022) ⚽️ and [ChatGPT](https://chat.openai.com/chat) have recently been the most popular subjects all across the world. The World Cup is the largest football event conducted every four years, and it is being held in Qatar this year, and ChatGPT is the natural language model for dialogue built by [OpenAI](https://openai.com/).

On 18 December 2022, the World Cup Final will be held in the [Lusail Stadium](https://www.qatar2022.qa/en/tournament/stadiums/lusail-stadium) of Lusail city. Lusail city was still desert in 2010 but the new municipality now includes an urban center and an artificial archipelago.

Left: Satellite image of Lusail city in 2010; Right: Satellite image of Lusail city in 2022 (Source: <https://www.bloomberg.com/graphics/2022-what-qatar-built-for-the-world-cup>): 
![](221215-chatgpt-1.webp)

As ChatGPT would have limited knowledge of the world after 2021, so I'm curious about how ChatGPT will introduce Lusail city. 🤔

![](/img/posts/221215-chatgpt-2.webp)

Anyway, let's try!

![](/img/posts/221215-chatgpt-3.webp)

It looks great! However, several World Cup aspects are currently missing.

Feed the contents of the answers to the Text-to-Image generator [Stable Diffusion](https://huggingface.co/spaces/stabilityai/stable-diffusion). 🎨

The World Cup element is still missing from the created visualization, as we can see.

![](/img/posts/221215-chatgpt-4.webp)

Okay! I would like to collect some latest information about Lusail city toward World Cup and share it with ChatGPT to see if it can gather more exciting news!

I created the scripts to parse the web contents from the following websites:

-   <https://www.qatar2022.qa/en/tournament/stadiums/lusail-stadium>
-   <https://www.bloomberg.com/graphics/2022-what-qatar-built-for-the-world-cup>
-   <https://en.wikipedia.org/wiki/Lusail>

Stored in a qatar-worldcup.csv file with described contents and parsed sources.

![](/img/posts/221215-chatgpt-5.webp)

Before we share the raw data with ChatGPT, let's run the **qatar-worldcup.csv** file through [PipeRider](https://infusesai.pse.is/4ntk57), a data reliability tool that can ensure data quality. 

We can examine the data characteristics in PipeRider's data report and discover that there are some **missing** and **duplicate** contents.

![](/img/posts/221215-chatgpt-6.webp)

![](/img/posts/221215-chatgpt-7.webp)

In **qatar-worldcup.csv**, there are numerous missing values as a result of the script's attempt to parse text from the image.

![](/img/posts/221215-chatgpt-8.webp)

As for the duplicates, they mainly resulted from the bug of retry logic in our parsing script.

![](/img/posts/221215-chatgpt-9.webp)

After fixing the known issues, the new data report now looks promising!

![](/img/posts/221215-chatgpt-10.webp)

Next, I used another script to automatically communicate parsed contents with ChatGPT. Here are some conversations.

![](/img/posts/221215-chatgpt-11.webp)

![](/img/posts/221215-chatgpt-12.webp)

![](/img/posts/221215-chatgpt-13.webp)

Cool! At the moment, it seems like our friend ChatGPT knows more about Lusail City in terms of the World Cup.

Let me ask the same question again!

![](/img/posts/221215-chatgpt-14.webp)

Excellent! The 2022 FIFA World Cup is included in the introduction of Lusail city!

Again, use the [Stable Diffusion](https://huggingface.co/spaces/stabilityai/stable-diffusion) to visualize Lusail city from the new ChatGPT's perspective.

![](/img/posts/221215-chatgpt-15.webp)

Fantastic! Despite the fact that it is far from the actual city of Lusail. 😂

But the visualization shows how much more realistically ChatGPT can explain how a city looks from a sports perspective and how it looks now.

When it becomes a football expert, which I believe it will, I will ask about its predictions for future World Cup champions. 🏆🏆🏆



