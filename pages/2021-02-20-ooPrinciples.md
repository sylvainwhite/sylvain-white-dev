---
layout: misc
title: "Oriented Object Principles"
author: "Sylvain White"
categories: subCategory
tags: [architecture, misc]
# image: city-2.jpg
---
<br/>


Based on [Head First - Design Patterns - A Brain-Friendly Guide](https://www.amazon.ca/Head-First-Design-Patterns-Brain-Friendly/dp/0596007124){:target="_blank"}

### OO Principles

* #### Basics
    * Abstraction
    * Encapsulation
    * Inheritance
    * Polymorphism

* #### Favor composition over inheritance
    * HAS-A relationship should be favored over IS-A relationship which is static
    * Composition allows to change behavior at initialization or runtime

* #### Program to interfaces not implementations
    * It doesn't mean necessarily Java interface
    * It could be an abstract class e.g. 'Animal' and the implementations 'Cat' and 'Dog'

* #### Strive for loosely coupled design between objects that interact
    * 'Loose coupling' means interacting objects have very little knowledge of each other

* #### Classes should be open for extension but closed to modification

    * Open for extension: 
        * Can sub-class
        * Easily used in composition
    * Closed to modification:
        * New behavior should not require to modifiy current class
        * Current behavior should be complete/coherent as it is

* #### Dependency inversion principle

    * High-level modules should not depend on low-level modules. Both should depend on abstractions 
    * [A crystal clear explanation... finally!](https://medium.com/@kedren.villena/simplifying-dependency-inversion-principle-dip-59228122649a){:target="_blank"}
    * [Why inverted ?](https://www.blinkingcaret.com/2016/01/27/inverts-dependency-inversion-principle/){:target="_blank"}
        > Thus, the dependency structure of a well designed object oriented program is “inverted” with respect to the dependency structure that normally results from traditional procedural methods.
 
* #### Principle of Least Knowledge

    * Talk only to your immediate friends
        * It means an object should only invoke methods that belong to:
            * The object itself
            * Objects passed in as a parameter to the method
            * Any object the method creates or instantiates
            * Any components of the object
        * Example:

![]({{ site.github.url }}/resources/objectOrientedPrinciples1.png "Principle of Least Knowledge")

* #### Single responsability

    * A class should have only one reason to change i.e. one responsability
    * More than one responsibility means more than one area of potential change
    * The term cohesion is used as a measure of how closely a class supports a single responsibility
    * High cohesion means the class is designed around a set of related functions
