---
layout: misc
title: "Branch Strategy"
author: "Sylvain White"
categories: subCategory
tags: [management]
---
<br/>

### Branch Strategy

Here is a simple branch strategy I used in many projects.

![]({{ site.github.url }}/resources/branchStrategy.png "Branch Strategy")

#### Summary

* All active development is performed in the main branch
* Once all features are done, a new release branch is created
* Release candidates (RC) are tested and fixed
* The last RC fully tested is the release (REL)
* Any fixes in the release branch is merged down into the main branch
