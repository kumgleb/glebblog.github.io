---
layout: post
title: Deconstructing a Frequent Misconception About Confidence Intervals
---

![_config.yml]({{ site.baseurl }}/images/confidence_intervals/logo.png)

# Deconstructing a Frequent Misconception About Confidence Intervals

## Step-by-step derivation of confidence intervals and how we often misinterpret them.

Confidence intervals are commonly used as a routine approach of interval estimation. If you’ve ever applied this approach, you may have come across this statement:

* For a 90% confidence interval, there is a 90% probability that a true parameter lies within that interval. <br>

Seems legit, doesn’t it? At least, it looked legit to me, at first. Well, it’s one of the most common misconceptions about confidence intervals. According to [1], 59% of surveyed researchers fall into this trap. And I was no exception.

So lets’s go back to square one and apply confidence intervals in a simple context and realize why this common misinterpretation is false. <br>

### Derivation of intervals
Let’s say we want to estimate the mean height of residents living in a city. Suppose that there are one million people living in this city, and their heights are normally distributed. Let’s assume that we know the true distribution parameters, say, the mean height is 1.8m and the standard deviation is 0.1m. These are the population parameters, which we usually do not know and want to estimate by our measurements.

![My helpful screenshot](/images/confidence_intervals/img_1.png)