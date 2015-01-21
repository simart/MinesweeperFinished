Minesweeper
==================

In this assignment you will be recreating the Microsoft Minesweeper game. If you are not familiar with minesweeper you should play the game until you are. You can find one version at [http://minesweeperonline.com/](http://minesweeperonline.com/)

Install the Guido Button Library
--------------------------------
We'll be using a GUI library called Guido. To install it, start *Processing* and choose *Sketch | Import Library | Add Library*. Type *Guido* in the search box, the click on *Guido by Florian Jenett* and then click *Install*.

Program Requirements
--------------------
1. Your minesweeper game will be a two dimensional array of buttons. Use constants for the number of rows and columns.
2. The number of bombs should also be specified by a constant.
3. Make sure all class member variables and methods are labeled appropriately as either `public`, `protected` or `private`
4. If you click on a button that contains a bomb, the game ends and all the bombs are displayed
5. If you click on a button that does not contain a bomb, a number appears at that location indicating the number of neighbors that DO contain bombs. Recall that each position has at most 8 neighbors. Note that the buttons on the boundary have fewer than 8 neighbors. For example, a corner has only three neighbors.
6. if the user clicks on a button and no number appears, then there are no bombs surrounding that button. Your program should then recursively keep marking those surrounding buttons that are not surrounded by bombs.
7. The game should end when all the buttons that do not contain bombs have been marked (assuming that you have not been blown up by then!)
8. Your game should use `Math.random()` to randomly place the mines.


Suggested steps to completing this assignment:
----------------------------------------------
1. Fork and clone down this repository
2. On line 4, create two integer constants `NUM_ROWS` and `NUM_COLS` and initialize them each with the value 20  
2. Go to line 18, use the constants to initialize the 2d array `buttons` to have 20 rows and 20 columns
2. Use nested loops to reate a `new MSButton` for each row column pair
2. Uncomment lines 55 and 56, You should now see a grid of buttons
2. Now, got to line 7, and initialize `bombs` to be a new empty ArrayList of `MSButton`  
3. Go to line 25 and write the `setBombs()` function. It should generate a random row and column number. Use the `contains()` function to check to see if  `buttons[row][col]` is already in `bombs`. If it isn't then `add` it
3. My program had the following additional methods, which I added in the following order:  
	* ``public boolean isValid(int row, int col)` returns `true` if (`row`,`col`) is a valid location on the grid and `false` otherwise
	* `public int countBombs(int row, int col)` counts the bombs in the 8 neighbors--(remember to check to see if the neighboring button is valid before checking to see if it's a mine)
	* `public boolean isWon()` determines if the player has won the game
	* `public void displayWinMessage()` uses `setLabel` to change the labels of the buttons to display a winning message
	* `public void displayLosingMessage()` displays the positions of all the bombs and displays a losing message
4. The `changeBackground` method is tricky: It should first check to see if the Button has already been clicked. If the button's background color is not (0,54,82) then return because the button has already been clicked. You can check the background color with code like: 
`buttons[row-1][col].getColor().getBackground() == color(0,54,82)`
If the button was a bomb, change it's background color to red with code like: 
`buttons[row][col].setColorBackground(color(255, 0, 0));` You can check if the ArrayList bombs contains the button that was clicked with code like: 
`if(bombs.contains(buttons[row][col]))`  

Otherwise change to the backgound of the button to something other than red, and then if has no neighboring bombs, it should recursively call itself with the valid neighboring positions that are "unclicked".


***
Alternative Assignment: The Game of Life
----------------------------------------
If you want an alternative to Minesweeper, you could write your own version of the The Game of Life. The Game of Life isn't what you think, it's a program that simulates how bacteria might grow. It's another program that is well suited to using a two dimensional array of buttons. You can find examples and descriptions at the following websites:
[http://www.bitstorm.org/gameoflife/](http://www.bitstorm.org/gameoflife/)
[http://www.math.com/students/wonders/life/life.html](http://www.math.com/students/wonders/life/life.html)

***
Samples of Student Work
-----------------------

