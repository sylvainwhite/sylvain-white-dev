---
layout: post
title: "Design Patterns"
author: "Sylvain White"
categories: architecture
tags: [architecture, misc]
# image: city-2.jpg
---
<br/>

## References

* Based on [Head First - Design Patterns - A Brain-Friendly Guide](https://www.amazon.ca/Head-First-Design-Patterns-Brain-Friendly/dp/0596007124){:target="_blank"}
* All 23 patterns from the Gang Of Four are presented here
* For a quick overview of all of them see [DZone Refcardz - Design Patterns]({{ site.github.url }}/resources/designPatternsDzoneRefcardz.pdf){:target="_blank"} 

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

<br/>

## Decorator

### Definition

* The **Decorator** Pattern allows for the dynamic wrapping of objects in order to modify their existing responsibilities and behaviors
 
### Advantages

* Attach additional responsabilities to an object dynamically
* Alternative when subclassing is impractical
* Specific functionality should not reside high in the object hierarchy

![]({{ site.github.url }}/resources/patternDecorator.png "Decorator Pattern")

### Sample code 

* [Client code](https://github.com/bethrobson/Head-First-Design-Patterns/blob/master/src/headfirst/designpatterns/decorator/starbuzz/StarbuzzCoffee.java){:target="_blank"}

* [Decorator code](https://github.com/bethrobson/Head-First-Design-Patterns/blob/master/src/headfirst/designpatterns/decorator/starbuzz/Mocha.java){:target="_blank"}

* [All code](https://github.com/bethrobson/Head-First-Design-Patterns/blob/master/src/headfirst/designpatterns/decorator/starbuzz){:target="_blank"}


<br/>

## Factory

### Definition

* The **Factory** Pattern defines an interface for creating an object, but lets subclasses decide which class to instantiate
 
### Advantages

* Factory method lets a class defer object creation to subclass
* Subclass may specify what objects should be created

![]({{ site.github.url }}/resources/patternFactory.png "Factory Pattern")

### Sample code 

* [Client code](https://github.com/bethrobson/Head-First-Design-Patterns/blob/master/src/headfirst/designpatterns/factory/pizzafm/PizzaTestDrive.java){:target="_blank"}

* [Factory method](https://github.com/bethrobson/Head-First-Design-Patterns/blob/master/src/headfirst/designpatterns/factory/pizzafm/PizzaStore.java){:target="_blank"}

* [Factory method subclass](https://github.com/bethrobson/Head-First-Design-Patterns/blob/master/src/headfirst/designpatterns/factory/pizzafm/NYPizzaStore.java){:target="_blank"}

 * [All code](https://github.com/bethrobson/Head-First-Design-Patterns/tree/master/src/headfirst/designpatterns/factory/pizzafm){:target="_blank"}


<br/>

## Singleton

### Definition

* The **Singleton** Pattern ensures a class has only one instance, and provides a global point of access to it
 
### Advantages

* The singleton controls access to a resource shared by the entire application
* Since the singleton creates the object, it might change the instantiation process

### Sample code. But not thread safe! 
```java
public class Singleton {
    private static Singleton uniqueInstance;
    // other useful instance variables here
    
    private Singleton() {}
    public static Singleton getInstance() {
        if (uniqueInstance == null) {
            uniqueInstance = new Singleton();
        }
        return uniqueInstance;
    }
    // other useful methods here
}
```

For more on threads and singleton: [Java Singleton Design Pattern](https://www.geeksforgeeks.org/java-singleton-design-pattern-practices-examples/){:target="_blank"}

* [Client code](https://github.com/bethrobson/Head-First-Design-Patterns/blob/master/src/headfirst/designpatterns/singleton/classic/SingletonClient.java){:target="_blank"}

 * [All code](https://github.com/bethrobson/Head-First-Design-Patterns/blob/master/src/headfirst/designpatterns/singleton/classic/){:target="_blank"}

<br/>

## Command

### Definition

* The **Command** Pattern encapsulates a request as an object, thereby letting you  parameterize other objects with different requests, queue or log requests, and support undoable operations.
 
### Advantages

* It decouples the classes that invoke the operation from the object that executes the operation
* It allows you to create a sequence of commands by providing a queue system
* New commands can be added awithout changing the existing code
* Macro command (list of commands) is easy to implement
* It can be used to define a rollback system in case of crash

![]({{ site.github.url }}/resources/patternCommand.png "Command Pattern")

### Sample code 

* [Client code](https://github.com/bethrobson/Head-First-Design-Patterns/blob/master/src/headfirst/designpatterns/command/undo/RemoteLoader.java){:target="_blank"}

* [Command interface](https://github.com/bethrobson/Head-First-Design-Patterns/blob/master/src/headfirst/designpatterns/command/undo/Command.java){:target="_blank"}

* [Concrete command](https://github.com/bethrobson/Head-First-Design-Patterns/blob/master/src/headfirst/designpatterns/command/undo/LightOffCommand.java){:target="_blank"}

**Check out the 'NoCommand' object** that is a 'null object' in remote control class

* [Remote control class](https://github.com/bethrobson/Head-First-Design-Patterns/blob/master/src/headfirst/designpatterns/command/undo/RemoteControlWithUndo.java){:target="_blank"}

* The NoCommand object is an example of a null object. A null object is useful
when you don’t have a meaningful object to return, and yet you want to remove
the responsibility for handling null from the client.

* [NoCommand class](https://github.com/bethrobson/Head-First-Design-Patterns/blob/master/src/headfirst/designpatterns/command/undo/NoCommand.java){:target="_blank"}

* [All code](https://github.com/bethrobson/Head-First-Design-Patterns/blob/master/src/headfirst/designpatterns/command/undo/){:target="_blank"}


<br/>

## Adapter

### Definition

* The **Adapter** Pattern converts the interface of a class into another interface the clients expect. Adapter lets classes work together that couldn’t otherwise because of incompatible interfaces
 
### Advantages

* Client is not complicated by having to use a different interface
* Adapter converts one interface to another while facade pattern makes it simpler

![]({{ site.github.url }}/resources/patternAdapter.png "Adapter Pattern")

### Sample code 

* [Client code](https://github.com/bethrobson/Head-First-Design-Patterns/blob/master/src/headfirst/designpatterns/adapter/ducks/DuckTestDrive.java){:target="_blank"}

* [Adapter class](https://github.com/bethrobson/Head-First-Design-Patterns/blob/master/src/headfirst/designpatterns/adapter/ducks/TurkeyAdapter.java){:target="_blank"}

* [All code](https://github.com/bethrobson/Head-First-Design-Patterns/blob/master/src/headfirst/designpatterns/adapter/ducks/){:target="_blank"}

<br/>

## Facade

### Definition

* The **Facade** Pattern provides a unified interface to a set of interfaces in a subsytem 
 
### Advantages

* Facade defines a higher-level interface that makes the subsystem easier to use
* Facade insulates the subsystem from the client

![]({{ site.github.url }}/resources/patternFacade.png "Facade Pattern")

### Sample code 

* [Client code](https://github.com/bethrobson/Head-First-Design-Patterns/blob/master/src/headfirst/designpatterns/facade/hometheater/HomeTheaterTestDrive.java){:target="_blank"}

* [Facade class](https://github.com/bethrobson/Head-First-Design-Patterns/blob/master/src/headfirst/designpatterns/facade/hometheater/HomeTheaterFacade.java){:target="_blank"}

* [All code](https://github.com/bethrobson/Head-First-Design-Patterns/blob/master/src/headfirst/designpatterns/facade/hometheater/){:target="_blank"}

<br/>

## Template Method

### Definition

* The **Template Method** defines the skeleton of an algorithm in a method deferring some steps to subclasses

### Advantages

* Subclasses can redefine certain steps of an algorithm without changing the
algorithm’s structure 
* Subclasses can define hooks to skip/modify steps of the algorithm
 
![]({{ site.github.url }}/resources/patternTemplateMethod.png "Template Method Pattern")

### Sample code 

* [Client code](https://github.com/bethrobson/Head-First-Design-Patterns/blob/master/src/headfirst/designpatterns/templatemethod/barista/BeverageTestDrive.java){:target="_blank"}

* [Template Method class](https://github.com/bethrobson/Head-First-Design-Patterns/blob/master/src/headfirst/designpatterns/templatemethod/barista/CaffeineBeverageWithHook.java){:target="_blank"}

* [Concrete Template Method class](https://github.com/bethrobson/Head-First-Design-Patterns/blob/master/src/headfirst/designpatterns/templatemethod/barista/CoffeeWithHook.java){:target="_blank"}

* [All code](https://github.com/bethrobson/Head-First-Design-Patterns/blob/master/src/headfirst/designpatterns/templatemethod/barista/){:target="_blank"}

<br/>

## Composite

### Definition

* The **Composite Method** allows you to compose objects into tree structures to represent part-whole hierarchies. Composite lets clients treat individual objects and compositions of objects uniformly.

### Advantages

* It allows to run behavior recursively over all components of an object tree
* It makes easier to you to add new kinds of components

![]({{ site.github.url }}/resources/patternComposite.png "Composite Pattern")

### Sample code 

* [Client code](https://github.com/bethrobson/Head-First-Design-Patterns/blob/master/src/headfirst/designpatterns/composite/menu/MenuTestDrive.java){:target="_blank"}

* [Component class](https://github.com/bethrobson/Head-First-Design-Patterns/blob/master/src/headfirst/designpatterns/composite/menu/MenuComponent.java){:target="_blank"}

* [Composite class](https://github.com/bethrobson/Head-First-Design-Patterns/blob/master/src/headfirst/designpatterns/composite/menu/Menu.java){:target="_blank"}

* [Leaf class](https://github.com/bethrobson/Head-First-Design-Patterns/blob/master/src/headfirst/designpatterns/composite/menu/MenuItem.java){:target="_blank"}

* [All code](https://github.com/bethrobson/Head-First-Design-Patterns/blob/master/src/headfirst/designpatterns/composite/menu/){:target="_blank"}

