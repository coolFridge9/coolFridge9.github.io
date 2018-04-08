---
layout: post
title: Tuples in C#
---

I used tuples to store coordinates on the board the first time I coded Tictactoe.

## intiialisation 
There are two ways to initialise tuples:
```csharp
Tuple<int, int> t1 = new Tuple<int,int>(x,y);
Tuple<int, int> t2 = Tuple.Create(x,y);
```

I prefer to use `Tuple.Create(x,y)` because you don't have to specify a type.

If you were to pass objects with a particular interface into a tuple than you would have to specify the type anyway.

for example: `tuple = Tuple.Create<IAnimal>(new Dog());` so it would be the same as `tuple = new Tuple<IAnimal>(new Dog())`

## accessing items
to access items in a tuple, you use `tuplename.itemx`

for example: the first item in a tuple would be accessed by `tuplename.item1` and the 2nd item would be `tuplename.item2`

one of my coworkers told me theres a way to change the names of the accessors.
