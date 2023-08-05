---
layout: misc
title: "WebSocket Heartbeat"
author: "Sylvain White"
categories: subCategory
tags: [protocols, architecture]
# image: city-2.jpg
---

<br/>

## WebSocket Heartbeat: networks are unreliable

Based on blog by Michael Hughes [[web](https://codinginthetrenches.com/2016/07/30/websocket-connection-closures-or-remember-that-networks-are-unreliable/){:target="_blank"}]

> Sometimes the link between the server and the client can be interrupted in a way that keeps both the server and the client **unaware of the broken state of the connection** (e.g. when pulling the cord) 

To avoid this problem:
* The classic solution is to use the ping message. See "How to detect and close broken connections?" [[web](https://github.com/websockets/ws){:target="_blank"}]
* Another solution - I think a cleaner one - is to use a 'uni-directional' heartbeat as suggested in Michaeal's blog 
