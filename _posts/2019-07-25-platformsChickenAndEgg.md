---
layout: post
title: "Chicken & Egg Problems"
author: "Sylvain White"
categories: misc
tags: [misc]
# image: city-2.jpg
---
<br/>

## Chicken & Egg Problems

A fabulous anecdote about Windows 95 and its backward compatibility from Joel Spolsky blog [Strategy Letter II: Chicken and Egg Problems](https://www.joelonsoftware.com/2000/05/24/strategy-letter-ii-chicken-and-egg-problems/){:target="_blank"}

> So. If you’re in the platform creation business, you are probably going to suffer from what is commonly known as the chicken and egg problem. Nobody is going to buy your platform until there’s good software that runs on it, and nobody is going to write software until you have a big installed base

> Windows 95? No problem. Nice new 32 bit API, but it still ran old 16 bit software perfectly. Microsoft obsessed about this, spending a big chunk of change testing every old program they could find with Windows 95. Jon Ross, who wrote the original version of SimCity for Windows 3.x, told me that he accidentally left a bug in SimCity where he read memory that he had just freed. Yep. It worked fine on Windows 3.x, because the memory never went anywhere. **Here’s the amazing part: On beta versions of Windows 95, SimCity wasn’t working in testing. Microsoft tracked down the bug and added specific code to Windows 95 that looks for SimCity. If it finds SimCity running, it runs the memory allocator in a special mode that doesn’t free memory right away. That’s the kind of obsession with backward compatibility that made people willing to upgrade to Windows 95.8.**

> You should be starting to get some ideas about how to break the chicken and egg problem: provide a backwards compatibility mode which either delivers a truckload of chickens, or a truckload of eggs, depending on how you look at it, and sit back and rake in the bucks.