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


### MOQ Framework
```csharp
 var moqVariable = new Mock<Interface>();
 moqVariable.Verify(x => x.Write(It.IsAny<string>()), Times.Exactly(3));
 ```
  
  It checks the output's a string and was outputted three times

### Edge of the world wrap and bug
To make the world wrap, I used modulus (dividing by the length/width) to make the square after the end square equal to the first square.

For example if the width of the grid was 3, then a cell in thew 3rd square should be neighbours with the cell in the first square. (so square 4 = square 1)

![_config.yml]({{ site.baseurl }}/images/Screen Shot 2018-05-21 at 3.53.52 PM.png)

with the formular in the image, I could make 4=1 and 0=3 which is what I needed for the wrap.

I discovered a bug when running the tests that the % operator in excel is different to the % operator in C# for negative numbers.  In regular modulus, -1%3 = 2 but in C# modulus, -1%3 = -1.  Luckily, I found this issue on Stackoverflow and someone had posted a formular to get the true modulus from c# modulus: `(x%m + m)%m`

everything else was pretty straight forward and problemless
