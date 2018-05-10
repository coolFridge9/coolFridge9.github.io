---
layout: post
title: Conways Game of Life 
---

## Classes
* Grid - Stores the Alive cells
* Cell - Stores the X and Y corordinates and knows if the cell is alive
* GridCreator - Has methods to create starting grids manually or randomly
* Renderer - Renders to text to the cmd
* CellChecker - Contains a method to tell if a cell should live in the next state
* GridUpdator - Runs though all the cells on the board and uses the CellChecker to create the grids next state
* Iterator - Runs a loop which continuosly updates and prints the grid
