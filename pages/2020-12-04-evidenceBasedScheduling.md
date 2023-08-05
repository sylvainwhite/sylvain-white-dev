---
layout: misc
title: "Evidence Based Scheduling"
author: "Sylvain White"
categories: subCategory
tags: [management]
# image: city-2.jpg
---
<br/>

## Evidence Based Scheduling (EBS)

* EBS is a software estimation approach created by Joel Spolsky [[web](https://www.joelonsoftware.com/2007/10/26/evidence-based-scheduling/){:target="_blank"}]
* EBS on Wikipedia [[web](https://en.wikipedia.org/wiki/Evidence-based_scheduling){:target="_blank"}]

<br/>
Core ideas of EBS:
* **Schedule**: Break the project into a list of tasks
    * Tasks should be very small so they can be estimated in hours 
    * Nothing longer than 16 hours
    * With small tasks, it will force you to actually design the program! See [Functional Specifications]({{ site.github.url }}/design/functionalSpecs.html){:target="_blank"}
    * Only the programmer doing the work can create the estimates
    * Don’t let managers badger developers into shorter estimates
* **Track**: Keep track of how long you spend working on each task
    * Don't track the exact time but elapsed time spent on the task
    * Even during interruptions, let the clock running as long as you work on the task
    * Over time, it is assumed that all interruptions will average out
    * Fix bugs as you find them. Charge the time back to the original task
* **Compute velocity** for each programmers
    * The velocity is the slope between Actual (i.e. tracked) hours versus Estimated hours
    * Velocity example from Joel Spolsky's blog:
    ![]({{ site.github.url }}/resources/EBSvelocity.png "Programmer velocity")

    * If the estimates are always exact, the velocity is 1
    * You need historical data to get accurate velocity
    * But not too old data since programmers get better at estimation 

* **Simulate**: Use the Monte Carlo simulation to get ship dates
    * The simulation is based on:
        * list of tasks along with their estimates
        * velocity of each programmers
    * It produces a chart of probability of shipping at any given date
    * Simulation example from Joel Spolsky's blog:
    ![]({{ site.github.url }}/resources/EBSsimulations.png "Monte Carlo simulations")

    * Comments on the graphic above:
        * The x-axis is when the calculation was done
        * The y-axis is the ship date
        * There are three curves here: 
            * the top one is the 95% probability date
            * the middle is 50%
            * the bottom is 5%
        * So, the closer the curves are to one another, the narrower the range of possible ship dates