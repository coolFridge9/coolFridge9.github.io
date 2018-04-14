---
layout: post
title: Tic Tac Toe
---

## First TicTacToe Iteration -Basic Version

The first time I coded TicTacToe. It was a 1 player game where you would play against an AI.

### logic and Implementation
I started by making the board a 2D array of integers


On the board: 
* O represented a blank space
* 1 represented a space filled by X
* 2 represented a space filled by O

I don't know why I used numbers instead of strings.  I could have plugged "X" and "O" straight into the array.

When it came to thinking of a win condition, I realised it would be easier to keep a list of 
moves for each player and use that movelist to decide if the player won.

This meant my code was keeping track of 2 boards which isnt very good coding.

### Win Condition
A players set of moves is stored as a list of tuples eg. [(1,1),(2,3)(3,3)]
#### Diagonal Win
my code would generate a list of moves required for a win based on the size of the board. For 
example, for a board of size 3, [(1,1),(2,2),(3,3)] would have to be included in a players move set for 
a left-to-right diagonal win.
#### Straight Line Win
Here are some possible Horizontal win move sets (Board size 3): ([1,2][2,2][3,2]) or ([2,3][1,3][3,3])
They all contain one Y value 3 times.

After sorting a users move set by Y value, You easily check if it contains the same value three times in a row.

I also implemented the same check for a vertical win using X values.

### AI
The AI had a method for generating a list of available spaces on the board.  It would loop through this list deciding what
move to make using the following logic:
1. If there is a move that could make the AI win, then this move is returned.  This could be checked by adding each move
to the players move list, checking for a win, then removing it from the move list.
2. If there is a move that can block a win, that move is returned. The AI can find this by adding each move on to
the human players move list, checking for a win, then removing the move from their move list.
3. Checks if the middle square is taken.  For even number board sizes eg 4X4, theres no middle sqare so it would be around
the middle.
4. Lastly, If none of the above moves could be made, the AI would choose a random square to take from the available spaces.

## Second Iteration TicTacToe Iteration - Flexible Version
This version was extremely flexible and allowed the user to go anywhere on an infinite board.  You could also add as many players as you wanted with any one-character symbols that you wanted.  In the main program.  you had to create a new game object and you could type game.AddPlayer("X",new Human()) and a new Human player would be added to the game.

### Board
This game didn't originally have a board structure.  Each player object held its own set of moves and had a didWin() function
to check if it won.  I ended up needing a board to check if a player move had already been taken. I created a Board object which held a list of every move that had been made.
