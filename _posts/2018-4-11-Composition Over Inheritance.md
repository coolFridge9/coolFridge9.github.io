---
layout: post
title: Composition Over Inheritance
---

Over my time here I have learned that inhertance is important to understand because it is used in many of our 
code bases but it shouldn't really be used due to a number of disadvantages which don't apply to composition. 

Inheritance makes it difficult to resuse methods outside of the inheritance branch which it is coded for.
Composition takes the idea that you have a library of methods and you can add them to an object.

### Implementation

You can do this by creating an interface type property in an object and create different classes which comply to that interface and assign objects to that interface which contain the methods.

### Testing

It can be quit useful for testing as you can create interfaces for specific functions such as inputs.  For example, Its difficult to unit test inputs from command line so you could make a test input class which calls the input from an object rather than the command line.

