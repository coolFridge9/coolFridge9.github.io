---
layout: post
title: Investigating why my mentors said I shouldn't use the build-in Point Structure 
---
I told my manager that my mentors wanted me to write a class for a cell instead of using the point structure and 
he told me to investigate why that was and write a blog post on it.

I started my investigation by googling what the difference between a Class and a Structure was.

### Class vs Structure
From my googling, I found out that Structs are values whereas Classes are references.

Structs should only be used when:
* Youre representing a single value (Simular to primative types)
* It has an instance size smaller than 16 bytes
* It is immutable 
* It will not have to be boxed frequently.
