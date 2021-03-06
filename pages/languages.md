---
layout: misc
title: Languages
---
<br/>

> There are only two kinds of languages: the ones people complain about and the ones nobody uses.

    Bjarne Stroustrup

<br/>

## Book: The C Programming Language' by Kernighan & Ritchie

Personal summary of the classic "The C Programming Language" by Brian W. Kernighan & Dennis M. Ritchie, Prentice Hall ed., 1988. Because I read it thoroughly many times. It is more nostalgia than anything else. Note the book was typeset with (pic|tbl|eqn|troff -ms) on a DEC VAX 8550. It says it all.
[[pdf]({{ site.github.url }}/resources/cLanguageKRSummary.pdf){:target="_blank"}]

<br/>

## Java Memory Leaks: Tools, Fixes, and More - DZone

Beware of Java memory leaks!

[[web](https://dzone.com/articles/how-to-find-and-fix-memory-leaks-in-your-java-appl){:target="_blank"}]
[[pdf]({{ site.github.url }}/resources/javaMemoryLeaks.pdf){:target="_blank"}]

<br/>

## Why we shouldn't comment out code

From the blog 'Deleting code' by Nat Batchelder [[web]](https://nedbatchelder.com/text/deleting-code.html){:target="_blank"} [[pdf]({{ site.github.url }}/resources/deletingCode.pdf){:target="_blank"}]

<br/>

## Lisp?

> "SQL, Lisp, and Haskell are the only programming languages that I've seen where one spends more time thinking than typing." <br>\- Philip Greenspun

Hmmmm... I am thinking of learning Lisp. Really.

<br/>

## What are the cultural differences between Unix and Windows programmers?

From the blog 'Biculturalism' by Joel Spolsky [[web]](https://www.joelonsoftware.com/2003/12/14/biculturalism/){:target="_blank"} 

> There are many details and subtleties, but for the most part it comes down to one thing: Unix culture values code which is useful to other programmers, while Windows culture values code which is useful to non-programmers.
<br/>...

> When Unix was created and when it formed its cultural values, there were no end users. Computers were expensive, CPU time was expensive, and learning about computers meant learning how to program. It’s no wonder that the culture which emerged valued things which are useful to other programmers. By contrast, Windows was created with one goal only: to sell as many copies as conceivable at a profit.

<br/>

## About functional programming

Rather long but very clear introduction paper on functional programming 'Functional Programming For The Rest of Us' by Slava Akhmechet [[web](https://www.defmacro.org/2006/06/19/fp.html){:target="_blank"}] [[pdf]({{ site.github.url }}/resources/functionalProgramming.pdf){:target="_blank"}]

<br/>

## JAVA: Execution in the Kingdoms of Nouns

A classic rant by Steve Yegge that resonates since 2006! It was kind of fixed
in Java 8 which includes lambda expression. It is still very verbose compared to other scripting languages. I think the essence of this beautifully written rant  [[web](http://steve-yegge.blogspot.com/2006/03/execution-in-kingdom-of-nouns.html){:target="_blank"}] is:

* Not everything is an object
> I've really come around to what Perl folks were telling me 8 or 9 years ago: "Dude, not everything is an object." It's odd, though, that Java4 appears to be the only mainstream object-oriented language that exhibits radically noun-centric behavior. 

* In some languages, it isn't the case
> You'll almost never find an AbstractProxyMediator, a NotificationStrategyFactory, or any of their ilk in Python or Ruby. Why do you find them everywhere in Java? 

* Solution: functional programming
> It's a sure bet that the difference is in the verbs. Python, Ruby, JavaScript, Perl, and of course all Functional languages allow you to declare and pass around functions as distinct entities without wrapping them in a class.

<br/>

## Very short functions are a code smell

[Very short functions are a code smell – an overview of the science on function length](https://softwarebyscience.com/very-short-functions-are-a-code-smell-an-overview-of-the-science-on-function-length/){:target="_blank"}

From the conclusion of this paper:

> Considering **that short functions tend to lead to longer debug times** and that very short functions tend **to have higher defect densities** (both in historical and modern datasets) the case for using very short functions becomes weak.

> As we could see from the historical studies, the definition of ‘short’ has changed over time. Still, if we focus on our dataset analysis to post-2000 data and studies and look at functions 1-3 lines long (short enough to be classified short in any study), the evidence is lopsided: there are few reasons for using them, and many reasons for not using them. **As such, software developers should be wary of breaking their code into too small pieces, and actively avoid introducing very short (1-3 lines)** functions when given the choice. At the very least unnecessary single-line functions (ie. excluding getters, setters etc.) should be all but banned.

The author is not as categoric for the optimal number of lines per function but he suggests something around 10 lines +/- 5 lines.