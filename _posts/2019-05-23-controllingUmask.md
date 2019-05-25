---
layout: post
title: "Controlling linux umask"
author: "Sylvain White"
categories: misc
tags: [misc]
# image: city-2.jpg
---
<br/>

## Controlling file permissions with umask

From 'Controlling file permissions with umask'on website 'linuxzoo' [[web](https://linuxzoo.net/page/sec_umask.html){:target="_blank"}]
[[pdf]({{ site.github.url }}/resources/controllingUmask.pdf){:target="_blank"}]

* Default permissions are assigned by the linux system whenever you create a new file or directory, and these are governed by the umask setting

* The umask serves to remove permissions as opposed to granting them. That is, the digits in the umask number are 'subtracted' from 777 for directories or 666 for files when you are creating their initial permissions



