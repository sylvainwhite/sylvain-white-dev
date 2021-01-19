---
layout: post
title: "On Bandwidth"
author: "Sylvain White"
categories: misc
tags: [misc]
# image: city-2.jpg
---
<br/>

### On Bandwidth for web developers

Few quotes from the document [An Engineer's Guide to Bandwidth]({{ site.github.url }}/resources/engineerGuideToBandwidth.pdf){:target="_blank"}

#### Packets, not bytes

> The quantum of internet transmission is not the bit or the byte, it's the packet.
Everything that happens on the 'net happens as discrete pachinko balls of regular
sizes. A message of N bytes is chopped into ceil(N / 1460) packets which are
then sent willy-nilly. That means there is little to no difference between sending 1
byte or 1,000. It also means that sending 1,461 bytes is twice the work of sending
1,460: two packets have to be sent, received, reassembled, and acknowledged.

#### Packet loss

> Packet loss manifests as packet latency. The odds are decent that a couple
packets that made up the copy of this article you are reading got lost along the
way. Maybe they had a collision, maybe they stopped to have a beer and forgot.The sending end then has to notice that a packet has not been acknowledged and
re-transmit.

##### Upstream < Downstream

> Internet providers lie. That "6 Megabit" cable internet connection is actually
6mbps down and 1mbps up. The bandwidth reserved for upstream transmission is
often 20% or less of the total available. This was an almost defensible thing to do
until users started file sharing, VOIPing, video chatting, etc en masse. Even
though users still pull more information down than they send up, the asymmetry
of their connections means that the upstream is a chokepoint that will probably
get worse for a long time.