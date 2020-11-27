---
layout: post
title: "Google Protocol Buffers"
author: "Sylvain White"
categories: protocols
tags: [protocols, architecture]
# image: city-2.jpg
---

<br/>

## Google protocol buffers definition

* Protocol Buffers (Protobuf) [[web](https://en.wikipedia.org/wiki/Protocol_Buffers){:target="_blank"}] is a method of serializing structured data
* It is used by applications to communicate with each other over a wire or for storing data 
* Protobuf includes a interface description language (IDL) that describes the structure of data 
* Protobuf generates source to generate/parse a stream of bytes based on description in IDL
* Protobuf is better than JSON in some cases [[web](https://codeclimate.com/blog/choose-protocol-buffers/){:target="_blank"}]
* Protobuf vs JSON performance comparison [[web](https://auth0.com/blog/beating-json-performance-with-protobuf/){:target="_blank"}]
* Sample code: client/server sending gRPC and JSON requests to a REST server [[web](https://medium.com/swlh/supercharge-your-rest-apis-with-protobuf-b38d3d7a28d3){:target="_blank"}]

<br/>

## gRPC: gRPC Remote Procedure Call

* In general, RPC is an interprocess communication technique to call a function in another process
* gRPC is based on Protobuf, HTTP/2 and IDL [[web](https://en.wikipedia.org/wiki/GRPC){:target="_blank"}]
* Features include:
    * authentication
    * bidirectional streaming
    * flow control
    * blocking or nonblocking bindings
    * cancellation and timeouts

* gRPC has four kinds of service method:
    * **Unary**: the client sends a single request and gets a single response back
    * **Server streaming**: the client sends a request and gets a stream to read a sequence of messages back. The client reads then stream until there are no more messages
    * **Client streaming**: the client sends a sequence of messages to the stream. It waits for the server to read them and return its response. 
    * **Bidirectional streaming**: Both the client and the server send a sequence of messages using a read-write stream. The two streams operate independently.

* gRPC needs a proxy to translate request from browsers to the gRPC server [[web](https://grpc.io/blog/state-of-grpc-web/#the-grpc-web-spec){:target="_blank"}]
* Notes on **Bidirectional streaming**
    * Bidirectional streaming is NOT available between server and browsers
    * Streaming is only available from server to browsers [[web](https://grpc.io/blog/state-of-grpc-web/#feature-sets){:target="_blank"}]
    * WebSocket allows bidirectional streaming between server and browsers
    * WebSocket is a communication protocol and not a RPC
    * To overview differences between HTTP 1.x, HTTP/2 and WebSocket [[web](https://www.infoq.com/articles/websocket-and-http2-coexist/){:target="_blank"}]
    * To understand differences between gRPC and WebSocket [[web](https://news.ycombinator.com/item?id=17278363){:target="_blank"}]
    
    


