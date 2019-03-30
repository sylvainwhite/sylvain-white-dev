---
layout: post
title: "About multithreading with shared data"
author: "Sylvain White"
categories: design
tags: [design,multithreading]
# image: city-2.jpg
---
<br/>

## About multithreading with shared data
 
I hate multithreading with shared data. I've spent weeks (and one poor friend spent months!) to fix weird and complex bugs with multithreading. I believe in some software gods who defend this statement: 

> **Douglas CrockFord** (The JavaScript god): “In systems programming threads are a necessary evil. In application programming they’re just evil.”

> **Peter Hintjens** (AMQP, ZeroMQ designer & developer): “It's a rare book that deserves burning, but most books on concurrent programming do”

> **Martin Odersky** (Developer of the Java compiler, Designer of Scala language): “If you're considering shared data and locks, it is helpful to recall the words of Harry Callahan, played by Clint Eastwood in the 1971 movie Dirty Harry: ‘I know what you're thinking. Did he fire six shots or only five? Well, to tell you the truth, in all this excitement I kind of lost track myself.But being as this is a .44 Magnum, the most powerful handgun in the world, and would blow your head clean off, you've got to ask yourself one question: Do I feel lucky? Well, do ya, punk?’”
        
[Dirty Harry - clip](https://www.youtube.com/watch?v=8Xjr2hnOHiM){:target="_blank"}

------------------------------------------------------

### Why multithreading is evil and how to leverage multicore if you don’t do multithreading?

[The problem with threads](https://www2.eecs.berkeley.edu/Pubs/TechRpts/2006/EECS-2006-1.pdf){:target="_blank"}

[The Painful State of the Art - in Multithreading magic](http://zeromq.org/blog:multithreading-magic){:target="_blank"}

------------------------------------------------------

### Why multithreading is evil for testing?

[Why might threads be considered evil](http://stackoverflow.com/questions/1191553/why-might-threads-be-considered-evil){:target="_blank"}

> What makes threads "evil" is that once you introduce more than one stream of execution into your program, you can no longer count on your program to behave in a deterministic manner. That is to say: Given the same set of inputs, a single-threaded program will (in most cases) always do the same thing. 
<br> 
<br/> 
A multi-threaded program, given the same set of inputs, may well do something different every time it is run, unless it is very carefully controlled. That is because the order in which the different threads run different bits of code is determined by the OS's thread scheduler combined with a system timer, and this introduces a good deal of "randomness" into what the program does when it runs.

------------------------------------------------------

### Multithreading with ZeroMQ

[ZeroMQ manual](http://zeromq.org/intro:read-the-manual){:target="_blank"}

> ZeroMQ is perhaps the nicest way ever to write multithreaded (MT) applications. Whereas ZeroMQ sockets require some readjustment if you are used to traditional sockets, ZeroMQ multithreading will take everything you know about writing MT applications, throw it into a heap in the garden, pour gasoline over it, and set it alight. It's a rare book that deserves burning, but most books on concurrent programming do. To make utterly perfect MT programs (and I mean that literally), we don't need mutexes, locks, or any other form of inter-thread communication except messages sent across ZeroMQ sockets.

------------------------------------------------------