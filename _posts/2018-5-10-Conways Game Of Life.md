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
