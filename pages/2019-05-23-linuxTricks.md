---
layout: misc
title: "Linux tricks"
author: "Sylvain White"
categories: subCategory
tags: [misc]
# image: city-2.jpg
---
<br/>

## Controlling file permissions with umask

From 'Controlling file permissions with umask' on website 'linuxzoo' [[web](https://linuxzoo.net/page/sec_umask.html){:target="_blank"}]
[[pdf]({{ site.github.url }}/resources/controllingUmask.pdf){:target="_blank"}]

* The umask is a linux command that sets the default permissions assigned by the linux system whenever you create a new file or directory. Ex:<br/>
`# umask 007`

* The umask serves to remove permissions as opposed to granting them. That is, the digits in the umask number are 'subtracted' from 777 for directories or 666 for files when you are creating their initial permissions

<br/>

## The spiped secure pipe daemon

Nice simple tool to create symmetrically encrypted and authenticated pipes between socket addresses. 
[[web](https://www.tarsnap.com/spiped.html){:target="_blank"}]

<br/>

## Unit testing for your bash script? <br/> (or python script, or ruby script or ...): scriptkeeper

From the web site [[web](https://github.com/Originate/scriptkeeper){:target="_blank"}]

> **scriptkeeper** is a tool for people who wish to write tests for existing scripts and/or use TDD to write new scripts. Because of its design, scriptkeeper is language agnostic, since it mocks out syscalls. That means you can test Bash scripts just as well as Python, Ruby, etc.