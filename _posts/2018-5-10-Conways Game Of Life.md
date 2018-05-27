---
layout: post
title: Conways Game of Life 
---

### how my class naming changed over the project

| Original Class Name | Purpose | CLass Name I changed it too by the end|
| ------------- |:-------------:| -----:|
| Grid   | Stores the Alive cells | LivingCellsGrid |
| Cell | Stores the X and Y corordinates and knows if the cell is alive | Location |
| GridCreator | Has methods to create starting grids manually or randomly | GridCreator |
| Renderer| Renders to text for the cmd | Renderer |
| CellChecker | Contains a method to tell if a cell should live in the next state | Deleted this class |
| GridUpdator | Runs though all the cells on the board and uses the CellChecker to create the grids next state | Generation |
| Iterator | Runs a loop which continuosly updates and prints the grid | ConwaysGameOfLife|


## WHY
I changed Grid to LivingCellsGrid because I wasn't storing dead cells in the grid so by specifying it was a living cells grid, it made variable naming in the class much simpler becasue I didn't have to specify alive cells in all the variable names in the class and it makes the intent of the class a lot more clear.



I changed Cell to Location because its only properties were X and Y integers so it was tecnically just a location.  storing the Location objects on the LvingCellsGrid really expressed intent because it became obvious that I was storing the locations of the alive cells



I deleted the CellChecker class because the name didn't express any obvious intent.  I also realised that the functions I was using to check the cells such as `CountAliveNeighbours()` and `ShouldLiveInNextGen()` didn't belong in this class and were better off in other classes.  I moved `CountAliveNeighbours()` to LivingCellsGrid and `ShouldLiveInNextGen()` to Generation.



I renamed GridUpdator to Generation because my mentor and I thought Generation.Next() was a beter way to get an updated grid using the domain language.



I ended up using ConwaysGameOfLife instead of Iterator because it used the domain language, Iterator was too technical.

### MOQ Framework
```csharp
 var moqVariable = new Mock<Interface>();
 moqVariable.Verify(x => x.Write(It.IsAny<string>()), Times.Exactly(3));
 ```
  
  It checks the output's a string and was outputted three times.
  
#### why is this useful??
It allows you to to do a unit test on a class which contains other classes.  By making the contained classes into mock classes, you can write a unit test which only tests the functionality of the single class you want to test.

### Edge of the world wrap and bug
To make the world wrap, I used modulus (dividing by the length/width) to make the square after the end square equal to the first square.

For example if the width of the grid was 3, then a cell in thew 3rd square should be neighbours with the cell in the first square. (so square 4 = square 1)

![_config.yml]({{ site.baseurl }}/images/Screen Shot 2018-05-21 at 3.53.52 PM.png)

with the formular in the image, I could make 4=1 and 0=3 which is what I needed for the wrap.

I discovered a bug when running the tests that the % operator in excel is different to the % operator in C# for negative numbers.  In regular modulus, -1%3 = 2 but in C# modulus, -1%3 = -1.  Luckily, I found this issue on Stackoverflow and someone had posted a formular to get the true modulus from c# modulus: `(x%m + m)%m`

everything else was pretty straight forward and problemless
