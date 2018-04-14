---
layout: post
title: Coding TicTacToe
---
![_config.yml]({{ site.baseurl }}/images/TicTacToe ImageC.png)
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

This meant my code was keeping track of the board twice which isn't ideal
### Win Condition
A players set of moves is stored as a list of tuples eg. [(1,1),(2,3)(3,3)]
#### Diagonal Win
my code would generate a list of moves required for a win based on the size of the board. For 
example, for a board of size 3, [(1,1),(2,2),(3,3)] would have to be included in a players move set for 
a left-to-right diagonal win.
#### Straight Line Win

![_config.yml]({{ site.baseurl }}/images/TicTacToe ImageC copy.png)

Here are some possible Horizontal win move sets (Board size 3): ([1,1][2,1][3,1]) or ([2,3][1,3][3,3])
They all contain one Y value 3 times.

After sorting a user's move set by Y value, You can easily check if it contains the same value three times in a row.

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

### Compostition
This code was the first time I used composition.  I created an interface which had a method for getting a player move. The human implentation of this interface would get a player move from the console and the AI implementation of this move would get its move from an AI object.

### Board
This game didn't originally have a board structure.  Each player object held its own set of moves and had a didWin() function
to check if it won.  I ended up needing a board to check if a player move had already been taken. I created a Board object which held a list of every move that had been made.  Each move was stored in a Move object which I created.

### Win Condition
Since The board was infinitely large in this iteration, I had to create a new win condition.
This win checker would loop though every move the player made and calculate the corosponding set needed for a win.

For example: (if the player needs 3 moves in a row to win)

Say the player made a move (2,2) 
* For a Horizontal win: The player needs moves (3,2) and (4,2)
* For a Vertical win: The player need moves (2,3) and (2,4)
* For a left-to-right diagonal win: The player need moves (3,3) and (4,4)
* For a right-to-left diagonal win: The player need moves (1,3) and (0,4)

![_config.yml]({{ site.baseurl }}/images/TicTacToe ImageC copy 2.png)

The win checker would check if any of the required move sets from each of the players moves were in the players moveset.

### AI
The AI for this was just random.  It would go somewhere near the last move that had been made.  I wanted to implement it to build up a train of moves but I never got around to it.

### Rendering
I remember running into a lot of problems rendering this board.  I would make the board a string before printing it so it could be unit tested.  It was a very difficult task since the players all held their own symbol and set of moves.  It wasnt all in one place.

I started off by rendering a 3x3 board so if you went off the board you would have to visualise it.  I rendered this by using all the players to build up a 2D array and then printed the 2D using a loop.

I wanted to make the board expandable so I created some functions which grabbed the maximum X and Y values needed and created an array large enough to hold all the moves.

Unfortunately arrays can't use negative indexes so I had to disallow negative moves for now.  

I plan on allowing negative moves in the future by using four arrays together one will hold positive moves, one will hold negatives moves, one will hold moves which are have a negative x and positive y, the other will hold moves with a positive x and a negative y.

## Third TicTakToe Iteration - Alot of Composition but still basic 3x3 board.
This TicTacToe game was built using recursion rather than an iterative gameplay loop as I did in the previous 2 versions.
 ### Board and Win Condition
I used a 2D string array for the board and used the same win condition as in my first Iteration.  I had to write a function to convert the 2D into lists to use the same win condition.

### Logic
So Basically valid input can be split into two types of valid inputs: Commands and Moves

Moves can be validated by being in the format x,y and both x and y have to be between 1 and 3.

Commands can be validated by being equal to "q" because the only command is press q to quit.

I created a validator interface which extended to a Moves validator and commands validator.  I then created a dictionary with the validator as the key and a gameplay executioner as the stored data. A executioner complied to an interface which had execute() as the required function.  

In the dictionary, The command validator corosponded to the command executioner which execute() would print a quit message and the game would end.

The move validator corosponded to the move executer which would add the move to the board, check if the game could continue and call the inputHandler.  Its confusing but the inputHandler accepts the dictionary of validators so the game keeps running recursively.

Im not finished this version but im thinking of adding a validator which checks if a move has been taken already because I haven't implemented that part yet.

### Testing
The previous two iterations, I skipped unit testing on some parts because it was too difficult to implement but now that I have a better understanding of composition, I was able to test almost everything. 

#### declining invalid input until a valid one is made
I created a test input reader which extended to the input reader interface so it could be substituted into my code instead of the input reader from the console.  You could pass through a list of strings into the test input reader and it had an index variable which would increment everytime an input was rejected.  For my test cases, I used Assert.Equal() on the index it was at when it returned a valid value.
