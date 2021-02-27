---
layout: post
title: "Peer code review"
author: "Sylvain White"
categories: quality
tags: [quality]
# image: city-2.jpg
---

<br/>

## Best Kept Secrets of Peer Code Review

Proven techniques to ensure succesful code reviews that don't waste developers' time 
[[pdf]({{ site.github.url }}/resources/peerCodeReview.pdf){:target="_blank"}]

Some excerpts from this book:

p.21 

> #### Fast review is effective 
It has also been shown that, when done properly, fast lightweight
code review can be just as effective as traditional meetings-based
inspections.

p.60 and following

> #### Review for at most one hour at a time
* Although not every study addressed this issue, a common result is that reviewers’ effectiveness at finding defects drops off precipitously after one hour.

> #### To detect more defects, slow down code readings
* To detect more defects, slow down code readings.
This might sound obvious; what’s not obvious is that this is by far the dominant factor in the number of defects detected.

> #### Inspection meetings need not be in person
* First, the vast majority of defects are found in the pre-meeting private “reading” phase. 
* Second, the primary result of a meeting is in sifting through and possibly removing false-positives .

p.72

> #### How fast should code be reviewed?
* If you go too fast you’re liable to miss defects. Industry experts say inspection rates should not exceed 200 lines per hour if you want an effective review. 

p.99 and following

> #### Famous Richard Feynman story

 > * In 1986 the space shuttle Challenger exploded 110.3 seconds after lift-off, killing all seven crew members. The subsequent presidential investigation sought to answer two questions: 
    * What caused the explosion?
    * Why wasn’t this prevented?
* The take-home point is this: Even with many, very intelligent and experienced people, mistakes will be made. NASA addressed this problem in nine parts, most of which are forms of review. 
* The point of software code review is the same – to eliminate as many defects as possible, regardless of who “caused” the error, regardless of who found it. This isn’t personal.

p.111

> #### The checklist is an important component of any review
* There are several ways to build a checklist; you’ll want to determine which technique is most appropriate for your development group.
* Checklists are most effective at detecting omissions. Omissions
are typically the most difficult types of errors to find.

p.115

> #### Measurement & Improvement
* You can't fix what you can't measure
* Raw measurements
    * LOC: line of codes
    * Inpection time
    * Defect count
* Analytical metrics
    * Inspection rate: LOC/hour
    * Defect rate: Defect count/hour
    * Defect density: Defect count/LOC
There are several ways to build a checklist; you’ll want to determine which technique is most appropriate for your development group.
* Checklists are most effective at detecting omissions. Omissions
are typically the most difficult types of errors to find.