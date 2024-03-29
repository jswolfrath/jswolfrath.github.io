---
title: Coping with Data Heterogeneity in Federated Learning
date: 2023-12-09
permalink: /posts/2023/federated-learning
exerpt_separator: <!--more-->
toc: true
tags:
 - Data Heterogeneity
 - Federated-Learning
---

Federated Learning (or, more generally, decentralized machine learning) is becoming increasingly important due to the geographically distributed nature of data. Data generated by IoT devices, video cameras, and mobile phones are often stored directly on the device or on nearby edge devices. It is infeasible to transfer all of this data to a centralized location for model training. Sending data over wide-area network (WAN) links is ofent slow and expensive. Futhermore, legal requirements and privacy regulations are becoming more prevalent, which restrict where data can be transferred and stored.

<!--more-->

Here is some additional text for the post. I am just typing random words on my keyboard now to try to force a line wrap on my monitor. Hopefully it looks OK.

[^replication]: I'm using 'replication' here to mean that the code used to generate quantitative results from a dataset should produce those same results when run by another researcher, *not* in the sense that means that independent researchers following the published protocol can collect the data themselves and arrive at the same conclusion.

# File paths

Anytime you load a dataset into R, you need to specify the path to that file. The same's true when you save R output to a file. This article started as a chapter of my dissertation, so all of the code originally lived in the Dissertation folder on my laptop. However, as I started adapting it to an article length manuscript, I created a new Conflict Preemption folder in my Projects folder. By the time the article was accepted, I had two main folders I needed to combine:

- `/Users/Rob/Dropbox/UNC/Dissertation/Onset`
- `/Users/Rob/Dropbox/WashU/Projects/Conflict Preemption`

Both of these folders live in my Dropbox, but that's about where the similarities end. I wrote most of the code for running models while still at UNC, so when I added new scripts to run models to respond to reviewer comments, I still stuck them in the UNC folder. That also means that all of the output of these models ended up in the UNC folder when it got transferred from the cluster. However, when I needed to do something simpler like create a time series plot of the number of separatist groups in existence, I wrote that code in the WashU folder. I also had a script in the WashU folder to load all of the results and generate plots from them. Because this script and the data it needed to load where in completely different directories, this is what I had to do to load the data to create one of the main figures:

```r
load('/Users/Rob/Dropbox/UNC/Dissertation/Onset/Figure Data/marg_eff_pop_df_cy.RData')
```
