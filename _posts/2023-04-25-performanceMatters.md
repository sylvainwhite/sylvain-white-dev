---
layout: post
title: "Performance Matters"
author: "Sylvain White"
categories: misc
tags: [misc]
# image: city-2.jpg
---
<br/>

### "Performance Matters" by Emery Berger [[web](https://www.youtube.com/watch?v=r-TLSBdHe1A){:target="_blank"}]

Very interesting video on 2 tools.

1. The first tool, named 'Stabilizer', allows you to better measure the execution speed of a program by eliminating factors which influence the results. Ex: CPU caching, layout in memory etc.

2. The second tool, named 'Coz', is a new approach to find which module of your program worth to be optimized. It gives you a percentage X of the overall speed improvement of your program given you can optimize a module by Y percentage. Brilliant!

According to the author:

> Since compiler optimizations have run out of steam, we need better profiling support, especially for modern concurrent, multi-threaded applications. Coz is a new "causal profiler" that lets programmers optimize for throughput or latency, and which pinpoints and accurately predicts the impact of optimizations. Coz's approach unlocks previously unknown optimization opportunities. Guided by Coz, we improved the performance of Memcached (9%), SQLite (25%), and accelerated six other applications by as much as 68%;