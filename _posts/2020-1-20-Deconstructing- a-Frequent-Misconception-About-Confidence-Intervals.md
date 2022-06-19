---
layout: post
title: Deconstructing a Frequent Misconception About Confidence Intervals
---

![_config.yml]({{ site.baseurl }}/images/confidence_intervals/logo.png)

### Introduction:
Confidence intervals are commonly used as a routine approach of interval estimation. If you’ve ever applied this approach, you may have come across this statement:

* For a 90% confidence interval, there is a 90% probability that a true parameter lies within that interval. <br>

Seems legit, doesn’t it? At least, it looked legit to me, at first. Well, it’s one of the most common misconceptions about confidence intervals. According to [[1]](http://www.ejwagenmakers.com/inpress/HoekstraEtAlPBR.pdf), 59% of surveyed researchers fall into this trap. And I was no exception.

So lets’s go back to square one and apply confidence intervals in a simple context and realize why this common misinterpretation is false. <br>

### Derivation of intervals:
Let’s say we want to estimate the mean height of residents living in a city. Suppose that there are one million people living in this city, and their heights are normally distributed. Let’s assume that we know the true distribution parameters, say, the mean height is 1.8m and the standard deviation is 0.1m. These are the population parameters, which we usually do not know and want to estimate by our measurements.

| ![space-1.jpg](/images/confidence_intervals/img_1.png) | 
|:--:| 
| *Distribution of heights for all the people living in the city.* |

Of course, if we measure the height of a million people, we can get the true mean value, and there is no need for any estimation at all. But in reality, we usually carry out a limited experiment and want to estimate real parameters using some limited sample from the whole population. <br>

Let’s suppose we take a subset of 50 random people and measure their height. These 50 people are a sample of our population. Let’s give them a code name “Subset-1”. We can estimate the mean height of all the people in the city by just calculating the mean height of Subset-1 (the sample mean). By doing so, we would get a so-called **point estimation**.


| ![Img_1](/images/confidence_intervals/img_2.png#center) | 
|:--:| 
| *Point estimation for the mean height of 50 random people.* |


However, if we take another random subset of 50 people, the value of the mean height would differ. Each random subset would give us a different result. How should we choose the one and only subset that would result in a better estimation of the true value? <br>

There is no way to determine which subset would give us a better result. In order to take such uncertainty into account, we can calculate an interval to estimate the true mean value. That would be a so-called **interval estimation**. <br>

#### Let’s find such an interval:
This is an estimation of the true mean height (the sample mean): 

<br>
![Img_1](/images/confidence_intervals/eq_1.png#center)
<br>

Different subsets of 50 people will produce different estimations, and that is why the mean height is also a random variable with some distribution. That is a sampling distribution of the sample mean with parameters:
<br>
![Img_1](/images/confidence_intervals/eq_2.png#center)
<br>
where **s** is an estimated standard deviation of the sample:
<br>
![Img_1](/images/confidence_intervals/eq_4.png#center)
<br>
For Subset-1, we get the following:

<br>
![Img_1](/images/confidence_intervals/eq_5.png#center)
<br>
Thus, for the mean height distribution based on Subset-1 we get:

<br>
![Img_1](/images/confidence_intervals/eq_6.png#center)
<br>

Let’s plot this distribution:

| ![Img_1](/images/confidence_intervals/img_3.png#center) | 
|:--:| 
| *An estimated distribution of the mean height for Subset-1.* |


We expect that the mean height value would follow the same distribution if we repeat our measurements with a different subset of people. For example, 90% of such measurements will match the interval [1.757; 1.803]. Let’s zoom in on the x axis and see it in the graph:


| ![Img_1](/images/confidence_intervals/img_4.png#center) | 
|:--:| 
| *Estimated distribution of the mean height of Subset-1.* |


**That is a 90% confidence interval for Subset-1.** <br>
We would get the same result if we used a commonly applied formula and the Z-table:

<br>
![Img_1](/images/confidence_intervals/eq_7.png#center)
<br>

So how can we interpret that 90% confidence level for the interval above? <br>

Taking the way this interval was formed into account, we may conclude that the interval covers 90% of the mean height measurements for 50 random people. So one can expect to find the mean height inside such an interval in 90% of all the future measurements. We can check it by drawing 100 random subsets of 50 people each, calculating the mean height and comparing it with our distribution:

| ![Img_1](/images/confidence_intervals/img_5.png#center) | 
|:--:| 
| *Red dashed lines — result of 100 repeatedly calculated mean heights by 50 random sampled people.* |

But such expectations are sure to fail to meet the reality. As we can see, the number of measurements (red dashed lines) falling outside of the estimated 90% interval is way bigger than 10. The reason is that we have calculated our interval based on some random sample mean. 90% of the observations will fall within the estimated interval only if it matches with the true one. We can plot the true interval as we know the true parameters:

<br>
![Img_1](/images/confidence_intervals/eq_8.png#center)
<br>

| ![Img_1](/images/confidence_intervals/img_6.png#center) | 
|:--:| 
| *Red dashed lines — result of 100 estimations, the mean heights of 50 random people.* |

But what will happen if we repeat our measurements and build a confidence interval for, say, 20 randomly sampled subsets of 50 people each? Here is what we will get:


| ![Img_1](/images/confidence_intervals/img_7.png#center) | 
|:--:| 
| *Blue lines — 90% confidence intervals for 20 random samples of 50 people each. Red dashed line — the true mean.* |

As one can see, 2 out of 20 confidence intervals do not include the true mean. Thus, if we continue conducting such an experiment, a chance that a given confidence interval will include the true parameter will tend to **90%**. That is what confidence level is all about. <br>

#### Now let’s return to the main question: 

***Can we say that once an interval is created, the true parameter (the mean height in our example) will fall within such an interval with a 90% probability?***
<br> 

The answer is no. There is no way to get such a probability. Once the interval is created, the true parameter is either inside or outside the interval, and no one can definitely determine where exactly it falls. We only can say how often such intervals may include the true mean, that is what confidence level is all about.

The nature of confidence intervals is that they can encompass the true value with some chance. In our example, a confident interval tends to encompass the true value in 90% of trials. But that does not mean that for some specific interval, there is a 90% chance of finding the true value within the interval.

Finally, let’s go to a primary source and find that Neuman (as the original proponent of confidence intervals) writes about it [[2]](http://gauss.stat.su.se/master/slht/probability_pdf/outline_of_a_theory_of_statistical_estimation_based_on_the_classical_theory_of_probability.pdf): <br>

*The theoretical statistician constructing confidence interval may be compared with the organizer of a game of chance in which the gambler has a certain range of possibilities to choose from while, whatever he actually chooses, the probability of his winning and thus the probability of the bank losing has permanently the same value, 1 — α. The choice of the gambler on what to bet, which is beyond the control of the bank, corresponds to the uncontrolled possibilities of true mean, having this or that value. The case in which the bank wins the game corresponds to the correct statement of the actual value of true mean. In both cases the frequency of “successes “ in a long series of future “games“ is approximately known. On the other hand, if the owner of the bank, say, in the case of roulette, knows that in a particular game the ball has stopped at the sector №1, this information does not help him in any way to guess how the gamblers have betted. Similarly, once the sample is drawn and the values of confident interval is determined, the calculus of probability adopted here is helpless to provide answer to the question of what is the true value inside.*

### Conclusion:
If you come across or need to calculate a confidence interval [a; b] with confidence level α, you need to remember that: <br>

* A confidence level does NOT imply that a probability of the true value falling within [a; b] is equal to α;
* A confidence level α is NOT a percentage of the sample data falling within [a; b];
* A confidence level α is NOT a percentage of experiments where the true mean would fall within [a; b].
<br>

Confidence level α means that by conducting repeated interval calculations using different samples, we will get a percentage of confidence intervals, including a true population parameter that tends towards α.

<br>
If you find some confidence intervals conceptions to be confusing, I encourage you to check out other misinterpretations and some research on them featured in this Wikipedia article [[3]](https://en.wikipedia.org/wiki/Confidence_interval#Meaning_and_interpretation).