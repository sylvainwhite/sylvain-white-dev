---
layout: misc
title: "Functional Specifications"
author: "Sylvain White"
categories: subCategory
tags: [design]
# image: city-2.jpg
---

<br/>

## Functional Specifications 

This is my personal summary of a serie of 4 papers by Joel Spolsky: Painless Functional Specifications 

### Part 1: Why bother? [[web](https://www.joelonsoftware.com/2000/10/02/painless-functional-specifications-part-1-why-bother/){:target="_blank"}] 

> The most important function of a spec is to design the program. Even if you are working on code all by yourself, and you write a spec solely for your own benefit, **the act of writing the spec — describing how the program works in minute detail — will force you to actually design the program**.

> The moral of the story is that when you design your product in a human language, it only takes a few minutes to try thinking about several possibilities, revising, and improving your design. Nobody feels bad when they delete a paragraph in a word processor. But when you design your product in a programming language, **it takes weeks to do iterative designs**

* Reasons to write specs:
    * To force designing the program: see quote above
    * To communicate: to programmers, QA , marketing, tech writers etc.
    * To make schedule: no schedule without specs

### Part 2: What’s a Spec? [[web](https://www.joelonsoftware.com/2000/10/03/painless-functional-specifications-part-2-whats-a-spec/){:target="_blank"}] 

> A functional specification describes how a product will work entirely from the user’s perspective. It doesn’t care how the thing is implemented. It talks about features. It specifies screens, menus, dialogs, and so on.

Not sure I agree with him but...

> Details are the most important thing in a functional spec. You’ll notice in the sample spec how I go into outrageous detail talking about all the error cases for the login page. 

He goes on what should and should not be part of the specs.

### Part 3: But… How? [[web](https://www.joelonsoftware.com/2000/10/04/painless-functional-specifications-part-3-but-how/){:target="_blank"}] 

In this part, Joel gives his advices on:
* who should write the specs
* how to run a software team

### Part 4: Tips [[web](https://www.joelonsoftware.com/2000/10/15/painless-functional-specifications-part-4-tips/){:target="_blank"}] 

Reading specs is often boring so Joel recommands...

> Tricking people into reading your stuff is usually just a matter of good writing. [...] Here are five easy rules that you absolutely must follow to make specs that get read.

* Rule 1: Be Funny

> If you read a lot of Dave Barry, you’ll discover that one of the easiest ways to be funny is to be specific when it’s not called for. “Scrappy pugs” are funnier than “dogs.” “Miss Piggy” is funnier than “the user”.

* Rule 2: Writing a spec is like writing code for a brain to execute

> So, when you’re writing a spec, try to **imagine the person you are addressing** it to, and try to imagine what you’re asking them to understand at every step. Sentence by sentence, **ask yourself if the person reading this sentence will understand it** at a deep level, in the context of what you’ve already told them

* Rule 3: Write as simply as possible

* Some hints:
    * Use the simplest language you can
    * Break things down to short sentences
    * Avoid walls of text
    * Use numbered or bulleted lists, pictures, charts, tables
    * ...and lots of whitespace so that the reading “looks” fluffier

* Rule 4: Review and reread several times

> Review and reread your spec several times, OK? When you find a sentence that isn’t super easy to understand, rewrite it.

* Rule 5: Templates considered harmful

> Have you ever read two good essays that could be fit into a template? Just drop the idea.