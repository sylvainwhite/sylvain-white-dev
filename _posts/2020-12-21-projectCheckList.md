---
layout: post
title: "Project Checklist"
author: "Sylvain White"
categories: management
tags: [management]
# image: city-2.jpg
---
<br/>

### Checklists for the preparation of the project

Based on [Software project best practices checklists](https://kkovacs.eu/software-project-best-practices-checklist){:target="_blank"} by Kristóf KOVÁCS and my own additions

<br/>

#### Specifications / Requirements / RFP

* Was thought given to the system administration functionality?
* Was thought given to error handling?
* Was thought given to logging? 
    * size, format, centralization, backup
* Does the specification clearly segregate the project into phases?
* Do all the phases have verifiable and  undisputable outcomes?
* Are all the phases shorter than a month? 
    * 1-3 weeks is optimal
* If there are interfaces, are the necessary data format specifications, API documentations all collected?
* For APIs, is there a versioning convention?
* Is the maximum load, bandwidth and cpu usage estimated?
* Are the security requirements specified? PCI requirements?
* To what extent and how the product should be scalable
* Should the product be hosted in the cloud or on premises?
* Are the operation and maintenance requirements specified?
* Does the product require per user permissions to operate/view/configure it?
* How does the configuration of the product work? 
* Are the education/training requirements specified?
* Are the installation/migration requirements specified?
* Is everything else collected?
    * Is there a brand manual?
    * Color guide? 
    * Design manual? 
    * Deployment requirements? 
    * The firm's ISO procedures? 
    * Related legislation?
* Are all the items - e.g. use cases - atomic and if possible measurable? 
    * For instance "fast" vs "10 sec"
* Is the specification the shortest and simplest possible, while still complete?

<br/>

#### Tools

Decide on your tools at the beginning:
* IDE - Integrated Development Environment
* source control
* build
* unit test
* load test
* code coverage
* code review
* linter
* web app server
* virtual machines
* bug tracker
* task tracking system

<br/>

#### Documentation

Define which docs are required:
* Developer documentation
    * requirements
    * design
    * project planning - deadlines, phases, resources
* Product documentation
    * user manual
    * operating manual
    * maintenance guide
    * quick start
    * API references
    * samples
    * how-to guides
    * concepts
    * resources 

<br/>

#### Price quote / Bid

* Are the specifications accepted by all stakeholders?
* Does every phase have a price quote?
    * 1-3 week long
* Are all outcomes/deliverables of phases clearly defined and testable? 
    * We're going to be paid based on these!
* Has the architecture and framework of the system already been decided?
    * At a minimum, programming languages and frameworks
* Will the allocated initial capital and the payment schedule together cover costs for the project's lifetime?
* Is there a quote for education/training?
* Is there a quote for installation/migration?
* Is there a quote for documentation?
* Is there a quote for operations and maintenance?
    * Projects rarely end with typing in the last line of code
* Is the contract attached?
* Who's going to own the software that is about to be developed?

<br/>

#### Project start

* Are the specifications still the same as at the time of the last price quote?
* Has the client signed the contract?   
    * Not "promised he will sign". Actually signed
* Are there developers and a project leader assigned to the project? 
    * Testers? 
    * Designer? 
    * Other experts as needed?
* Do we have a reachable and decision-capable contact person at the client?
* Does the development team have consensus and clear vision about what will be the final delivery?
* Does everybody on the team know about the client, the project, the constraints and the deadline?
* Are you going to use Agile? 
    * Set sprint length in advance

<br/>

#### Checklists for development - General principles

* Does everyone remember the KISS principle and Occam's razor?
     * KISS: "Keep it simple, stupid"
     * Occam's razor: "The simplest explanation or strategy tends to be the best one"
* Is UTF-8 used for everything? All should be UTF-8
    * Databases. Tables. DB connections. Strings. Content-type, etc.
* Are compilation and any code generation automated? 
    * Makefile, Ant, Maven, etc.
* Does every piece of input that comes from an untrusted sources gets filtered?
    * Untrusted sources: user or other systems
    * Invalid characters, invalid type, etc.
* Do we prevent the users from uploading dangerous files?
* Are all forms validated for consistency on the server side? 
    * As needed, on the client side also
* Is all the code processed through a linter?
* Is the code sufficiently - but not overly - commented?
* Do you have a standard virtual machine to develop/deploy/test your product?

<br/>

#### Task Tracking

* Does the team has a task tracking system in place?
* Is the task tracking system painless enough to use? 
* Is the task tracking system viewed often enough both by team members and management?
* Can everybody assign tasks to everybody?
    * For instance, developers assigning tasks to management or sales
* Is there some way to request acceptance testing?

<br/>

#### Source control

* Is the project using source control?
* Does everyone agree on a branching strategy?
* Is it easy to create a full working instance after checkout/clone?
    * Add an ./init.sh for setting permissions
    * Makefile for code generation
* Is there a database initialization script in the repository?  
    * Database structure must be under source control too
* Do people pull/fetch/update before committing?
    * Most source control systems force you to, but not all
    * One should always integrate before commit
* Does every commit contains only one modification?
* Does every commit have a description? 
    * Nobody will remember in three months what "today's work" was
* Was the new code tested and automated tests run before committing?
    * At some places, the person who commits code that breaks the compilation/autotests has to pay for next day's coffee/dinner
* If the database needed changing, was the db creation script modified and committed?

<br/>

#### Testing

* Does the system have automated tests?
* Are the tests under source control?
* Do the tests work the system on as many components as possible?       
    * For web-based systems tests that use the user interface directly are better than unit tests, since the former also tests the communication and the client-side javascript
* Are the tests work in a test database, that gets reset at the start to a known state?

<br/>

#### Checklist for operations and maintenance

* Is there an automated monitoring/alert system in place?
* Will you know if the automated monitoring system breaks down?
    * Is something watching the automated monitoring system?
* Were the development features deactivated in the deployed code?
    * For instance, error/exception display, default passwords, etc
* Does every operational project has one person who is responsible?
* Is that responsible person subscribed to the security list of all the technologies used in that project?
* When making small modifications to operational code or configuration, is it always clearly noted why and when the modification happened, who did it, who asked for it, and, if feasible, what was the original?
* Are abandoned/dead projects taken offline?
