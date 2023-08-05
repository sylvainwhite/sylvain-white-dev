---
layout: misc
title: "Architecture"
author: "Sylvain White"
categories: mainCategory
tags: [architecture]
---
<br/>

## About multithreading with shared data
 
I hate multithreading with shared data. I've spent weeks (and one poor friend spent months!) to fix weird and complex bugs with multithreading. I believe in some software pundits who defend this statement: 

> **Douglas CrockFord** (The JavaScript god): “In systems programming threads are a necessary evil. In application programming they’re just evil.” [[web](http://borys.musielak.eu/douglas-crockford-on-threads){:target="_blank"}]

> **Peter Hintjens** (AMQP, ZeroMQ designer & developer): “It's a rare book that deserves burning, but most books on concurrent programming do” [[web](https://www.oreilly.com/library/view/zeromq/9781449334437/ch02s06.html){:target="_blank"}]

> **Martin Odersky** (Developer of the Java compiler, Designer of Scala language): “If you're considering shared data and locks, it is helpful to recall the words of Harry Callahan, played by Clint Eastwood in the 1971 movie Dirty Harry: ‘I know what you're thinking. Did he fire six shots or only five? Well, to tell you the truth, in all this excitement I kind of lost track myself. But being as this is a .44 Magnum, the most powerful handgun in the world, and would blow your head clean off, you've got to ask yourself one question: Do I feel lucky? Well, do ya, punk?’” [[web](https://www.artima.com/pins1ed/actors-and-concurrency.html){:target="_blank"}]
[[Dirty Harry - clip](https://youtu.be/8Xjr2hnOHiM?t=93){:target="_blank"}]

> **Joel Splosky** (blogger, co-founder of Stack Overflow): “And [Eric S. Raymond](http://web.stanford.edu/~ouster/cgi-bin/papers/threads.pdf){:target="_blank"} has convinced me that threads are usually not as good a solution as separate processes: indeed years of experience have shown me that programming with multiple threads creates much additional complexity and introduces whole new categories of dangerously frightful heisenbugs” [[web](https://www.joelonsoftware.com/2003/12/01/craftsmanship-2/){:target="_blank"}] 

> **Edward A. Lee** (Professor, University of California at Berkeley): “  Although threads seem to be a small step from sequential computation, in fact, they represent a huge step.  They discard the most essential and appealing properties of sequential computation: understandability,  predictability,  and determinism. Threads, as a model of computation, are wildly nondeterminisim” (nondeterminisim : Given the same set of inputs, a program doesn't give always the same results) "...To offer a third analogy, a folk definition of insanity is to do the same thing over and over again and to expect the results to be different. By this definition, we in fact require that programmers of multithreaded systems be insane. Were they sane, they could not understand their programs." [[web](https://www2.eecs.berkeley.edu/Pubs/TechRpts/2006/EECS-2006-1.pdf){:target="_blank"}]

------------------------------------------------------

### Why multithreading is evil for development?

[The problem with threads](https://www2.eecs.berkeley.edu/Pubs/TechRpts/2006/EECS-2006-1.pdf){:target="_blank"}

[The Painful State of the Art - in Multithreading magic](http://zeromq.org/blog:multithreading-magic){:target="_blank"}

> A technical article from Microsoft titled "Solving 11 Likely Problems In Your Multithreaded Code" demonstrates how painful the state of the art is. [...] The article says, "correctly engineered concurrent code must live by an extra set of rules when compared to its sequential counterpart." This is putting it mildly. The developer enters a minefield of processor code reordering, data atomicity, and worse. Let's look at what those "extra rules" are. Note the rafts of new terminology the poor developer has to learn.

------------------------------------------------------

### Why multithreading is evil for testing?

[Why might threads be considered evil](http://stackoverflow.com/questions/1191553/why-might-threads-be-considered-evil){:target="_blank"}

> What makes threads "evil" is that once you introduce more than one stream of execution into your program, you can no longer count on your program to behave in a deterministic manner. That is to say: Given the same set of inputs, a single-threaded program will (in most cases) always do the same thing. 
<br> 
<br/> 
A multi-threaded program, given the same set of inputs, may well do something different every time it is run, unless it is very carefully controlled. That is because the order in which the different threads run different bits of code is determined by the OS's thread scheduler combined with a system timer, and this introduces a good deal of "randomness" into what the program does when it runs.

------------------------------------------------------

### But I must program a multithreaded application

Here a some suggestions:

[ZeroMQ manual](http://zeromq.org/intro:read-the-manual){:target="_blank"}

> ZeroMQ is perhaps the nicest way ever to write multithreaded (MT) applications. Whereas ZeroMQ sockets require some readjustment if you are used to traditional sockets, ZeroMQ multithreading will take everything you know about writing MT applications, throw it into a heap in the garden, pour gasoline over it, and set it alight. It's a rare book that deserves burning, but most books on concurrent programming do. To make utterly perfect MT programs (and I mean that literally), we don't need mutexes, locks, or any other form of inter-thread communication except messages sent across ZeroMQ sockets.

[OpenMP](http://zeromq.org/intro:read-the-manual){:target="_blank"}

> OpenMP uses a portable, scalable model that gives programmers a simple and flexible interface for developing parallel applications for platforms ranging from the standard desktop computer to the supercomputer.An application built with the hybrid model of parallel programming can run on a computer cluster using both OpenMP and Message Passing Interface (MPI), such that OpenMP is used for parallelism within a (multi-core) node while MPI is used for parallelism between nodes

[Intel® Threading Building Blocks](https://software.intel.com/en-us/intel-tbb){:target="_blank"}

> Threading Building Blocks (TBB) is a C++ template library developed by Intel for parallel programming on multi-core processors. Using TBB, a computation is broken down into tasks that can run in parallel. The library manages and schedules threads to execute these tasks

------------------------------------------------------
<br/>

## Summary of Model-View-Controller architecture

Personal summary of MVC architecture [[pdf]({{ site.github.url }}/resources/summaryMvcArchitecture.pdf){:target="_blank"}] based on:

* [Android Architecture by Thanos Karpouzis](https://android.jlelse.eu/android-architecture-2f12e1c7d4db){:target="_blank"}
* [MVC, MVP and MVVM: The Ideas by Sergei Tachenov](http://www.tachenov.name/2016/09/30/208/){:target="_blank"}

<br/>

## How To Build Utterly Reliable Systems

From blog by Pieter Hintjens [[web]](http://imatix.wikidot.com/articles:how-to-build-utterly-reliable-systems){:target="_blank"} [[pdf]({{ site.github.url }}/resources/utterlyReliableSystems.pdf){:target="_blank"}]

Here are some excerpts that strike me the most:

**Pieces need to fit people** Ultimately, architecture is about fitting the problem to people. If a problem fits neatly to one developer or one small team, it has a good size. If a problem can only be solved by collaborating teams, it's badly sized.

**Interfaces define the fracture points** It's best to slice at the point where the interface is simplest. The interface will become a contract between individual developers, or teams. The simplest contract is the best one.

**Every problem can be deconstructed** If an architect cannot break a large problem into pieces, he or she is not competent. Sometimes lateral thinking is needed. But we have never seen large problems that could not be divided up.

**The architecture is a contract** It must be clear enough to create boundaries, between teams and layers, that cannot and never need to be crossed except through agreed interfaces.

**Decouple the change process** The architecture should package change into clean boxes so that the overall system can be both stable and dynamic.

**One page architecture** One of my rules is: the architecture of any system, no matter how big, can fit onto one page. And I don't mean, using a 3pt typeface.

Practically, it means:

* Divide and Conquer
* Formalize the Interfaces
* Identify and Eliminate Risk
* Eliminate Dependencies
* Ensure Full Testability

<br/>

## From STUPID to SOLID Code!

The theory of SOLID principles was introduced by Robert C. Martin in his 2000 paper Design Principles and Design Patterns. 

SOLID is an acronym that stands for five basic principles of OO design:

* Single Responsibility Principle
* Open/Closed Principle
* Liskov Substitution Principle
* Interface Segregation Principle
* Dependency Inversion Principle

Here is a neat article by William Durand explaining it in a funny way [[web]](https://williamdurand.fr/2013/07/30/from-stupid-to-solid-code/){:target="_blank"}

<br/>

## Broker versus Brokerless architecture: a comparison

Short and super clear comparison between both approaches [[web]](http://zeromq.org/whitepapers:brokerless){:target="_blank"}

<br/>

## How do you structure your apps?

There is no recipe to build a good architecture but here are few good
advices to build one. See slides 'How do you structure your apps?' [[pdf]({{ site.github.url }}/resources/howDoYouStructureYourApps.pdf){:target="_blank"}] by Kat Zien

<br/>

<!-- ## See also posts on architecture

{% for page in site.tags["architecture"] %}
  - {{ page.title }}
{% endfor %}

{% for post in site.tags["architecture"] %}
  <a href="{{ site.github.url }}{{ post.url }}">{{ post.title }}</a>
{% endfor %} -->
