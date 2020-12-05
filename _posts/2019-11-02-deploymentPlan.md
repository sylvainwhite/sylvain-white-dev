---
layout: post
title: "Deployment plan"
author: "Sylvain White"
categories: management
tags: [management]
# image: city-2.jpg
---
<br/>

## Deployment plan

From 'Scalable Internet Architectures' by Theo Schlossnagle, Sams Publishing, 2006

> A successful push plan has four parts: a plan to get from A to B, a plan to get from B to A, a plan to restore A from bare metal, and a successful test of the first two. (Testing a bare metal restore for every push would be suicide, or at least leave you constantly contemplating it.) Although it is always a good idea to have a tested plan for reverting a change (backing out a push), in a rapid development environment it is fundamental. Rapid development often leads to less testing and quality assurance, which means that changes are pushed, and bad things happen. 