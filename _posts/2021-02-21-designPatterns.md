---
layout: post
title: "Design Patterns"
author: "Sylvain White"
categories: architecture
tags: [architecture, misc]
# image: city-2.jpg
---
<br/>

Based on [Head First - Design Patterns - A Brain-Friendly Guide](https://www.amazon.ca/Head-First-Design-Patterns-Brain-Friendly/dp/0596007124){:target="_blank"}

<br/>

## Strategy

### Definition

* The **Strategy** Pattern defines a family of algorithms,
encapsulates each one, and makes them interchangeable.
Strategy lets the algorithm vary independently from
clients that use it

### Advantages

This pattern allows to:
* Encapsulates a family of algorithms into own set of classes
* Change algorithm at runtime

![]({{ site.github.url }}/resources/patternStrategy.png "Strategy Pattern")

### Sample code 

* [Client code](https://github.com/bethrobson/Head-First-Design-Patterns/blob/master/src/headfirst/designpatterns/strategy/Duck.java){:target="_blank"}

* [All code](https://github.com/bethrobson/Head-First-Design-Patterns/blob/master/src/headfirst/designpatterns/strategy){:target="_blank"}

<br/>

## Observer

### Definition

* The **Observer** Pattern defines a one-to-many
dependency between objects so that when one
object (subject) changes state, all of its dependents 
(observers) are notified and updated automatically.

### Advantages

This pattern follows the 'loose coupling' principle. 'Loose coupling' means interacting objects have very little knowledge of each other. How?:
* The only thing the subject knows about an observer is that it
implements an interface
* New observers can be added/removed at any time
* Never need to modify the subject to add new types of observers
* Can reuse subjects or observers independently of each other.
* Changes to either the subject or an observer will not affect the other
* Java has already classes that implement this pattern

![]({{ site.github.url }}/resources/patternObserver.png "Observer Pattern")

### Sample code 

* [Client code](https://github.com/bethrobson/Head-First-Design-Patterns/blob/master/src/headfirst/designpatterns/observer/weather/WeatherData.java){:target="_blank"}

* [All code](https://github.com/bethrobson/Head-First-Design-Patterns/tree/master/src/headfirst/designpatterns/observer/weather){:target="_blank"}