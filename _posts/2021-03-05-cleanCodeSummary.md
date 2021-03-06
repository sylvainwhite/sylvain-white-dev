---
layout: post
title: "Clean Code Summary"
author: "Sylvain White"
categories: quality
tags: [quality, design]
# image: city-2.jpg
---
<br/>

## Clean Code: A Handbook of Agile Software Craftsmanship

* Below is a my personal summary of [Clean Code by Robert Martin](https://www.amazon.ca/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882){:target="_blank"}

<br/>

### Names 

#### Class Names
Classes and objects should have noun or noun phrase names like Customer , WikiPage ,
Account , and AddressParser . Avoid words like Manager , Processor , Data , or Info in the name of a class. A class name should not be a verb.

#### Method Names
Methods should have verb or verb phrase names like postPayment , deletePage , or save .
Accessors , mutators, and predicates should be named for their value and prefixed with get , set , and is according to the javabean standard.

#### Use Solution Domain Names
So go ahead and use computer science (CS) terms, algorithm names, pattern names, math terms, and so forth. It is not wise to draw every name from the problem domain because we don’t want our coworkers to have to run back and forth to the customer asking what every name means when they already know the concept by a different name.

#### Pick One Word per Concept
Pick one word for one abstract concept and stick with it.

<br/>

### Functions

### Function length
Functions should not be 100 lines long. Functions should hardly ever be 20 lines long.

### Functions shoud do one thing
THEY SHOULD DO IT WELL. THEY SHOULD DO IT ONLY.

### One Level of Abstraction per Function
In order to make sure our functions are doing “one thing,” we need to make sure that the statements within our function are all at the same level of abstraction.

### Switch statement
My general rule for switch statements is that they can be tolerated if they appear only once, are used to create polymorphic objects, and are hidden behind an inheritance
relationship so that the rest of the system can’t see them. Of course every circumstance is unique, and there are times when I violate one or more parts of that rule.

### Function Arguments
The ideal number of arguments for a function is zero (niladic). Next comes one (monadic), followed closely by two (dyadic). Three arguments (triadic) should be avoided where possible. More than three (polyadic) requires very special justification—and then shouldn’t be used anyway.

### Flag Arguments
Flag arguments are ugly. Passing a boolean into a function is a truly terrible practice. It immediately complicates the signature of the method, loudly proclaiming that this function does more than one thing.

### Prefer Exceptions to Returning Error Codes
Returning error codes from command functions is a subtle violation of command query
separation. It leads to deeply nested if/then structures. When you return an error code, you create the problem that the caller must deal with the error immediately.

On the other hand, if you use exceptions instead of returned error codes, then the error processing code can be separated from the happy path code and can be simplified.

**BUT** try/catch blocks are ugly in their own right. They confuse the structure of the code and mix error processing with normal processing. So it is better to extract the bodies of the try and catch blocks out into functions of their own.

### DRY: Don't repeat yourself
Duplication may be the root of all evil in software.

<br/>

## Comments

### Explain Yourself in Code
There are certainly times when code makes a poor vehicle for explanation. Unfortunately, many programmers have taken this to mean that code is seldom, if ever, a good means for explanation. This is patently false. 
Which would you rather see? This:
```java
    // Check to see if the employee is eligible for full benefits
    if ((employee.flags & HOURLY_FLAG) && (employee.age > 65))
```
Or this?
```java
    if (employee.isEligibleForFullBenefits())
```
In other words, don’t use a comment when you can use a function or a variable.

<br/>

## Formatting

### How big should a source file be?
It appears to be possible to build significant systems out of files that are **typically 200 lines long, with an upper limit of 500**. Although this should not be a hard and fast rule, it should be considered very desirable.

### Variable Declarations
Variables should be declared as close to their usage as possible. Instance variables, on the other hand, should be declared at the top of the class.

### Dependent Functions
If one function calls another, they should be vertically close, and the caller should be above the callee, if at all possible.

### Line length
This suggests that we should strive to keep our lines short. The old Hollerith limit of
80 is a bit arbitrary, and I’m not opposed to lines edging out to 100 or even 120. But
beyond that is probably just careless.

### Don't return null
Prefer an object that handles this special case. See [Special Case Pattern](https://www.blog.jamesmichaelhickey.com/Practical-Coding-Patterns-For-Boss-Developers-Special-Case/){:target="_blank"} from Martin Fowler. See also in this blog the [Null Object in Design Patterns post]({{ site.github.url }}/architecture/designPatterns.html){:target="_blank"}. Fortunately, Java has Collections.emptyList() , and it returns a predefined immutable list that we can use for this purpose:
```java
    public List<Employee> getEmployees() {
        if( .. there are no employees .. )
            return Collections.emptyList();
    }
```
If you code this way, you will minimize the chance of NullPointerExceptions and your
code will be cleaner.

### Don’t Pass Null
Returning null from methods is bad, but passing null into methods is worse.

<br/>

## Boundaries

### Use Third-party Code

Let's say we have this code:

```java
    Map<Sensor> sensors = new HashMap<Sensor>();
    ...
    Sensor s = sensors.get(sensorId );
```

Passing an instance of Map<Sensor> liberally around the system means that there will
be a lot of places to fix if the interface to Map ever changes. It might be better to encapsulate it in a class.

```java
    public class Sensors {
        private Map sensors = new HashMap(); 
        public Sensor getById(String id) {
            return (Sensor) sensors.get(id);
        }
    }
```

The interface at the boundary ( Map ) is hidden. It is able to evolve with very little impact on the rest of the application. 

**BUT** we are not suggesting that every use of Map be encapsulated in this form. Rather, we are advising you not to pass Map s (or any other interface at a boundary) around your system. If you use a boundary interface like Map , keep it inside the class, or close family of classes, where it is used. Avoid returning it from, or accepting it as an argument to, public APIs.

### Learning Tests Are Better Than Free
The learning tests end up costing nothing. We had to learn the API anyway, and writing
those tests was an easy and isolated way to get that knowledge. The learning tests were
precise experiments that helped increase our understanding.

Not only are learning tests free, they have a positive return on investment. **When there are new releases of the third-party package, we run the learning tests to see whether there are behavioral differences**.

### Using Code That Does Not Yet Exist

A number of years back I was part of a team developing software for a radio com-
munications system. There was a subsystem, the “Transmitter,” that we knew little
about, and the people responsible for **the subsystem had not gotten to the point of defining their interface**.

To keep from being blocked, **we defined our own interface**. We called it something
catchy, like Transmitter . We gave it a method called transmit that took a frequency and a data stream. **This was the interface we wished we had**.

**Once the transmitter API was defined**, we wrote the TransmitterAdapter to bridge the gap. The ADAPTER encapsulated the interaction with the API and provides a single place to change when the API evolves.

![]({{ site.github.url }}/resources/cleanCodeAdapter.png "Transmitter Adapater")

<br/>

## Classes

### Class Organization
Following the standard Java convention, a class should begin with a list of variables. Public static constants, if any, should come first. Then private static variables, followed by private instance variables. There is seldom a good reason to have a public variable.

### Constants versus Enums

Enums in Java are very powerful tools that allow much more expression and flexibility than constantts e.g. final int. Consider this variation on the payroll code:

```java
    public class HourlyEmployee extends Employee {
        private int tenthsWorked;
        HourlyPayGrade grade;
        public Money calculatePay() {
                int straightTime = Math.min(tenthsWorked, TENTHS_PER_WEEK);
                int overTime = tenthsWorked - straightTime;
                return new Money(
                    grade.rate() * (tenthsWorked + OVERTIME_RATE * overTime)
                );
            }
            ...
    }
    public enum HourlyPayGrade {
        APPRENTICE {
            public double rate() {
                return 1.0;
            }
        },
        LEUTENANT_JOURNEYMAN {
            public double rate() {
                return 1.2;
            }
        },
        JOURNEYMAN {
            public double rate() {
                return 1.5;
            }
        },
        MASTER {
            public double rate() {
                return 2.0;
            }
        };
        public abstract double rate();
    }
```