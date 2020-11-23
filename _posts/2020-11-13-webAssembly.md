---
layout: post
title: "Web Assembly"
author: "Sylvain White"
categories: architecture
tags: [architecture]
# image: city-2.jpg
---

<br/>

## Web Assembly: How and why

Excellent paper from Milica Mihajlija
[[web](https://blog.logrocket.com/webassembly-how-and-why-559b7f96cd71//){:target="_blank"}] 
<br/>Here are my takeaways:

1. Web Assembly is textual language easily transformed into binary code that is delivered to the browser
* .wat file contains the textual form of Web Assembly
* .wasm file contains the binary code of Web Assembly

2. Many high level languages have compilers to generate the Web Assembly binary code (.wasm file)
* Examples of languages generating wasm: C, C++, Rust, Go, Python, Java, PHP

3. The binary code (.wasm file) is executed by the Javascript engine in the browser
* Examples of Javascript engines executing wasm: V8, SpiderMonkey, JavaScriptCore, Chakra

4. Web Assembly interacts with JavaScript in the browser 
* Examples in C, C++, Rust [[web](https://www.tutorialspoint.com/webassembly/webassembly_examples.htm){:target="_blank"}] 
* Example with more details in C++ [[web](https://www.freecodecamp.org/news/get-started-with-webassembly-using-only-14-lines-of-javascript-b37b6aaca1e4/){:target="_blank"}] 

5. Web Assembly interacts with JavaScript both ways: 
* JavaScript can call Web Assembly functions
* Web Assembly functions can call Javascript code

6. The Web Assembly has been designed for:
* performance (it is much better than Javascript for calculation)
* portability (it runs on all major browsers)
* flexibility (it can be written in many high level languages)

7. Note on performance:
* The execution time of WASM binaries is just 20% slower than the execution of same native code
