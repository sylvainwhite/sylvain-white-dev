---
layout: post
title: "Javascript Promises"
author: "Sylvain White"
categories: javascript
tags: [javascript]
# image: city-2.jpg
---
<br/>

## Javascript promises

Here is code that shows the behavior of Promises in different
cases: return or not, call resolve() or not etc. It's worth
to take few minutes to look at the code. There are surprising cases.

```js
function log(msg){console.log(msg);}

var p1 = new Promise((resolve, reject) => {
            resolve("p1 - resolved");
        });

var p2 = new Promise((resolve, reject) => {
            resolve("p2 - resolved");
        });

var p3 = new Promise((resolve, reject) => {
            return "p3 - returned";
        });

var p4 = new Promise((resolve, reject) => {
            reject("p4 - rejected");
        });

var p5 = new Promise((resolve, reject) => {
            reject("p5 - rejected");
        });
  
var p6 = new Promise((resolve, reject) => {
            resolve("p6 - resolved");  
        });

function test6(){
  return p6.then((msg) => {
            log(msg);
            return "p6 - 1st then() returned";
        })
        .then((msg) => {
            log(msg);
            return "p6 - 2nd then() returned";
        })
        .catch(log);
}

var p7 = new Promise((resolve, reject) => {
            reject("p7 - rejected"); 
        });

function test7(){
  return p7.then(() => {
            return "p7 - 1st then() returned";
        })
        .then((msg) => {
            log(msg);
            return "p7 - 2nd then() returned";
        })
      .catch((msg) => {
            log("p7 - 1st catch: " + msg);
        });
}

var p8 = new Promise((resolve, reject) => {
            reject("p8 - rejected"); 
        });

function test8(){
  return new Promise((resolve, reject) => { 
      p8.then((msg) => {
            log(msg);
            return "p8 - 1st then() returned";
        })
        .then((msg) => {
            log(msg);
            resolve("p8 - 2nd then() resolved");
        })
      .catch((msg) => {
            log("p8 - 1st catch: " + msg);
            reject(msg);
        });
  });
}

var p9 = new Promise((resolve, reject) => {
        reject("p9 - rejected"); 
    });

function test9(){
  return p9.then((msg) => {
            log(msg);
            return "p9 - 1st then() returned";
        })
        .then((msg) => {
            log(msg);
            return "p9 - 2nd then() returned";
        })
      .catch((msg) => {
            log("p9 - 1st catch: " + msg);
            return Promise.reject(msg);
        });
}

var p10 = new Promise((resolve, reject) => {
        resolve("p10 - resolved"); 
    });

function test10(){
  return new Promise((resolve, reject) => { 
      p10.then((msg) => {
            log(msg);
            return "p10 - 1st then() returned";
        })
        .then((msg) => {
            log(msg);
            resolve("p10 - 2nd then() resolved");
        })
      .catch((msg) => {
            log("p10 - 1st catch: " + msg);
            reject(msg);
        });
  });
}

var p11 = new Promise((resolve, reject) => {
        resolve("p11 - resolved"); 
    });

function test11(){
  return p11.then((msg) => {
        log(msg);
            return "p11 - 1st then() returned";
        })
        .then((msg) => {
            log(msg);
            return "p11 - 2nd then() returned";
        })
      .catch((msg) => {
            log("p11 - 1st catch: " + msg);
            return Promise.reject(msg);
        });
}

var p12 = new Promise((resolve, reject) => {
        resolve("p12 - resolved"); 
    });

function test12(){
  return p12.then((msg) => {
            log(msg);
            return "p12 - 1st then() returned";
        })
        .then((msg) => {
            log(msg);
            return "p12 - 2nd then() returned";
        })
      .catch((msg) => {
            log("p12 - 1st catch: " + msg);
            return Promise.reject(msg);
        });
}

var p13 = new Promise((resolve, reject) => {
        resolve("p13 - resolved");  
    });

var p14 = new Promise((resolve, reject) => {
    reject("p14 - rejected"); 
});     
        
function test14(){
  return p14.then((msg) => {
            log(msg);
            return "p14 - 1st then() returned";
        })
        .then((msg) => {
            log(msg);
            return "p14- 2nd then() returned";
        })
      .catch((msg) => {
            log("p14 - 1st catch: " + msg);
            return "p14 - catch() returned";
        });
}

var p15 = new Promise((resolve, reject) => {
    resolve("p15 - resolved"); 
});

function test15(){
    return p15.then((msg) => {
        log(msg);
        // Even if there is no return here
        // This then() returns a resolved promise
    });
}
   
// Tests
p1.then(log);

p2.then(log)
.then(() => {
    console.log("p2 ---then() always returns a resolved promise");
});

p3.then(log); // return doesn't resolve so .then(log) never called

p4.catch(log)
.then(() => {
    console.log("p4 ---catch() always returns a resolved promise");
});

p5.catch((msg) => {
    log("p5 - 1st catch: " + msg);
    return Promise.reject("p5 - promise rejected from 1st catch");
})
.catch((msg) => {
    log("p5 - 2nd catch: " + msg);
});

test6().then(log);

test7().catch((msg) => {
    log("p7 - 2nd catch: " + msg); // never called. The error is not 'rethrown'
});

test8().catch((msg) => {
    log("p8 - 2nd catch: " + msg);
});

test9().catch((msg) => {
    log("p9 - 2nd catch: " + msg);
});

test10().then(log)
.catch((msg) => {
    log("p10 - 2nd catch: " + msg);
});

test11().then(log)
.catch((msg) => {
    log("p11- 2nd catch: " + msg);
});

test12().then(log)
.catch((msg) => {
    log("p12 - 2nd catch: " + msg);
});

p13.then(log)
.catch(log)
.then(() => {
    log("p13 ---catch() always returns a resolved promise. EVEN if not called in chain!!!");
});

test14().then((msg) => {
    log("p14 ---catch() always returns a resolved promise: " + msg);
});

test15().then((msg) => {
    log("p15 ---then() without 'return' returns a resolved promise: " + msg);
});
```

Run it with repl.it

<iframe height="400px" width="100%" src="https://repl.it/repls/EcstaticClosedWordprocessor?lite=true" scrolling="no" frameborder="no" allowtransparency="true" allowfullscreen="true" sandbox="allow-forms allow-pointer-lock allow-popups allow-same-origin allow-scripts allow-modals"></iframe>