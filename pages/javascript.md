---
layout: misc
title: Javascript
---

## Javascript: The keyword 'This'

The keyword 'This' is always tricky. Here are two very good articles by to unveil the mystery! 
* [The Keyword "this" for Beginners by Brandon Morelli](https://codeburst.io/javascript-the-keyword-this-for-beginners-fb5238d99f85){:target="_blank"}
* [Understanding the "this" keyword in JavaScript by Nick](http://unschooled.org/2012/03/understanding-javascript-this/){:target="_blank"}

<br/>

## ES6 - Javascript course summary

This is a document [[pdf]({{ site.github.url }}/resources/es6JavascriptCourseSummary.pdf){:target="_blank"}] I wrote to summarize the excellent ES6 pluralsight javascript course [[web](https://www.pluralsight.com/courses/javascript-fundamentals-es6){:target="_blank"}]

<br/>

## Javascript memory leaks? Yes. It can happen

How to track and fix javascript memory leaks by Sebastian Peyrott

[4 Types of Memory Leaks in JavaScript and How to Get Rid Of Them](https://auth0.com/blog/four-types-of-leaks-in-your-javascript-code-and-how-to-get-rid-of-them/){:target="_blank"}

<br/>

## The Weird History of JavaScript

A very clean summary on youtube of the Javascript history famously made in 10 days... 

[The Weird History of JavaScript](https://www.youtube.com/watch?v=Sh6lK57Cuk4){:target="_blank"}

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

<br/>

## Explanation of JavaScript prototype property

**Warning**: Rather old but still valuable. Doesn't include ES6 syntax 

References:
1. Good explanation of prototype: 
[http://dmitrysoshnikov.com/ecmascript/javascript-the-core/](http://dmitrysoshnikov.com/ecmascript/javascript-the-core/){:target="_blank"}

2. \_\_proto\_\_ versus prototype: 
[https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Object/proto](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Object/proto){:target="_blank"}

```js
// -Three ways to create Object in JavaScript
var a = {firstName: "Elvis", lastName: "Presley", songs: {"blues": "It's now or never", "rock": "Blue suede shoes"}}; // literal
var b = new Object({firstName: "Elvis", lastName: "Presley", songs: {"blues": "It's now or never", "rock": "Blue suede shoes"}}); // equivalent to literal
var c = Object.create(a); // create a shallow copy of object a

console.log("1: " + a.lastName);
console.log("2: " + b.lastName);
console.log("3: " + c.lastName);

// -Modify object c. Note object c is a SHALLOW COPY of object a
// -Shallow copy vs deep copy: https://we-are.bookmyshow.com/understanding-deep-and-shallow-copy-in-javascript-13438bad941c
// -c.lastName is a 'real' copy and not a reference to object a
// -c.songs is a reference to object songs a not a 'real' copy
c.lastName = "Gratton"; // modifies only object c
a.songs.rock = "Jailhouse rock"; // we modify object a so it modifies also object c

console.log("----------------");
console.log("4: " + a.lastName);
console.log("5: " + b.lastName);
console.log("6: " + c.lastName);
console.log("7: " + c.songs.rock);

// -Every JavaScript object has a prototype. The prototype is also an object
// -All JavaScript objects inherit their properties and methods from their prototype
// -Object literal or with new Object() inherit from a prototype called Object.prototype
// -Other basic object types have their own prototype
// -For instance, objects created with new Date() inherit the Date.prototype

// -You can create your own constructor function to build new Objects
// -By convention, it always starts with a capital letter. For instance:
function Person(firstName, lastName) {
    this.firstName = firstName; // these properties are not part of the prototype object!
    this.lastName = lastName;
}

// We can add properties and functions to the prototype separately
Person.prototype.code = "007";
Person.prototype.introduce = function() {
  return "My name is " + this.lastName + ", " + this.firstName + " " + this.lastName;
};

// Create an object with the Person function we just defined
var d = new Person("James", "Bond");

console.log("----------------");
console.log("8: " + d.lastName);
console.log("9: " + d.introduce());
console.log("10: " + d.code);

// -In the prototype object, there is always the function constructor to create the object
// -Note: Object.getPrototypeOf(x).constructor is the function itself
//        Object.getPrototypeOf(x).constructor.name is the name of the function

console.log("----------------");
console.log("11: " + Object.getPrototypeOf(a).constructor.name);
console.log("12: " + Object.getPrototypeOf(d).constructor.name);

// We can create a new object from an existing object or from the prototype since prototype is an object itself
var e = Object.create(d); // from an existing object
var f = Object.create(Person.prototype); // from the prototype
e.firstName = "Ingrid";
e.lastName = "Bergman";

console.log("----------------");
console.log("13: " + Object.getPrototypeOf(e).constructor.name);
console.log("14: " + Object.getPrototypeOf(f).constructor.name);
console.log("15: " + e.introduce());
console.log("16: " + e.code);
console.log("17: " + f.code);
// -Don't forget: the constructor function has not been called on object f
// -So, firstName and lastName are undefined
console.log("18: " + f.introduce());

// -Prototypes are chained (prototype has prototype that has prototype etc... up to Object.prototype)
// -With Person, we have a simple example of chaining of 2 prototypes

console.log("----------------");
console.log("19: " + Object.getPrototypeOf(d).constructor.name);
console.log("20: " + Object.getPrototypeOf(Object.getPrototypeOf(d)).constructor.name);

// -When accessing a property/function on an object, javaScript first looks in the object itself
// -If it doesn't find it, it looks in the prototype chain
// -For instance, let's define the property 'code' in the object itself
e.code = "006";

console.log("----------------");
console.log("21: " + e.code);
delete e.code; // Then, delete it
console.log("22: " + e.code); // It falls back to the prototype chain

// The prototype allows you to add functions to basic JavaScript types (or any type actually)
String.prototype.trim = function() {
  return this.replace(/^\s+|\s+$/g, "");
};

// Define a simple String which now has the trim() function by default
var g = "     Super duper     ";

console.log("----------------");
console.log("23: '" + g + "'");
console.log("24: '" + g.trim() + "'");

// -Inheritance - the ugly way
// -Since prototypes are chained, it can be used for inheritance
// -But this kind of inheritance is NOT recommended. Why?
//  1. We don't need it - See Douglas Crockford - JavaScript the Good parts
//  2. ES6 has a new syntax to avoid it - not shown here
function Teacher(firstName, lastName, subject) {
  Person.call(this, firstName, lastName); // call the 'super' constructor
  this.subject = subject;
}

// ... but we need to fix the prototype... ugly!
Teacher.prototype = Object.create(Person.prototype); // here is the classic inheritance
Teacher.prototype.constructor = Teacher;
var h = new Teacher("Douglas", "Crockford", "JavaScript");

console.log("----------------");
console.log("25: " + h.subject);
console.log("26: " + h.introduce());

// -Inheritance - the Crockford way (note there are other inheritance patterns)
// -Build an object, create a copy and modify it. It is differential inheritance by opposition to the classic inheritance
var person = {
    init: function(firstName, lastName) {
      this.firstName = firstName;
      this.lastName = lastName;
    },
    introduce:  function() {
      return "My name is " + this.lastName + ", " + this.firstName + " " + this.lastName;
    }
};

var teacher = Object.create(person);
teacher.setSubject = function(subject) {
  this.subject = subject;
};

teacher.teach = function() {
    return this.introduce() + " and I am teaching " + this.subject;
};

var t = Object.create(teacher);
t.init("Richard", "Feynman");
t.setSubject("physics");

console.log("----------------");
console.log("27: " + t.teach());
```

Run it with repl.it

<iframe height="400px" width="100%" src="https://repl.it/repls/AnnualBlissfulDifference?lite=true" scrolling="no" frameborder="no" allowtransparency="true" allowfullscreen="true" sandbox="allow-forms allow-pointer-lock allow-popups allow-same-origin allow-scripts allow-modals"></iframe>