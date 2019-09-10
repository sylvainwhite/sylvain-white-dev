---
layout: post
title: "Javascript Prototype"
author: "Sylvain White"
categories: javascript
tags: [javascript]
# image: city-2.jpg
---
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