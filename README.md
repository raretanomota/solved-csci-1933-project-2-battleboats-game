Download Link: https://assignmentchef.com/product/solved-csci-1933-project-2-battleboats-game
<br>
Battleboats is a probability-based board game that challenges the user to locate enemy boats hidden on a rectangular grid. The purpose of the game is to locate and destroy every enemy boat in the least number of guesses.

1. BOARD

You will be modelling this game in Java. There are no requirements for the actual classes and functions you design, but you <strong>must implement every part of the description below</strong>. Your code may also be judged based on style. This should not be a stressful requirement – it simply means that you must create logically organized, well-named and well-commented code so the TAs can grade it.

<strong>You are required to specify which main method we should run </strong>in a comment in the file. This is because there may be multiple main methods. A good way to make this obvious is to make a Main.java class that contains only a main method.

IMPORTANT: You cannot import anything to help you complete this project. The only exception is importing Scanner to handle the I/O. Note that you do not have to explicitly import Math because Java already does it for you. In other words, you can use Math methods without importing Math

Note: You are not required to write tests for your code; however, you will find it useful to write your own tests to prove to yourself that your code works. <strong>Please include any test classes you write with your submission</strong>.

<h1>1      Board</h1>

The computer will simulate a square <em>n </em>× <em>n </em>board. <strong>You are required to use a 2-dimensional array to represent the board</strong>. The type of this array is up to the programmer.

The user will select whether they want to play the game on <strong>Standard </strong>or <strong>Expert </strong>mode when the program starts. If <strong>Standard </strong>mode is selected, the program should create a board of <strong>8 </strong>rows by <strong>8 </strong>columns. If <strong>Expert </strong>mode is selected, the program should create a board of <strong>12 </strong>rows by <strong>12 </strong>columns. Assume that the points in the normal mode board range from (0<em>,</em>0) to (7<em>,</em>7) inclusive, and from (0<em>,</em>0) to (11<em>,</em>11) inclusive in the hard mode.

Hint: You may find it useful to make your own BattleboatsBoard class that contains a constructor to set up the array and all the methods for setting up boats.

<h1>2       Boats</h1>

Each boat is represented by a line of consecutive squares on the board. Boats may not overlap other boats, extend outside the game board, or be placed diagonally. They may be horizontal or vertical. A boat is considered “sunk” when all the squares of the boat have been “hit” by the user.

<h2>3. TURNS</h2>

Examples: Valid coordinates for a boat of size 3 are {(0<em>,</em>0)<em>,</em>(0<em>,</em>1)<em>,</em>(0<em>,</em>2)} and {(1<em>,</em>1)<em>,</em>(2<em>,</em>1)<em>,</em>(3<em>,</em>1)}. Examples of invalid coordinates are {(0<em>,</em>0)<em>,</em>(0<em>,</em>1)}, which is invalid because there are not enough points. {(0<em>,</em>0)<em>,</em>(0<em>,</em>2)<em>,</em>(0<em>,</em>3)} is invalid because the points are not consecutive. {(−1<em>,</em>0)<em>,</em>(0<em>,</em>0)<em>,</em>(1<em>,</em>0)} is invalid because the first coordinate is out of bounds.

Finally, two boats cannot contain the same point because they cannot overlap.

After the game mode has been chosen and the game board has been correctly sized, <strong>the program should place boats randomly on the board</strong>. This requires randomly generating a coordinate (<em>x,y</em>) where the boat will be placed as well as randomly choosing whether the boat should be horizontal or vertical. The quantity of boats is defined by the width and height of the game board.

For the <strong>Standard </strong>game mode you will place <strong>5 </strong>boats on the board. These boats will have the following lengths:

<ul>

 <li>1 boat of length 5</li>

 <li>1 boat of length 4</li>

 <li>2 boats of length 3</li>

 <li>1 boat of length 2</li>

</ul>

For the <strong>Expert </strong>game mode you will place <strong>10 </strong>boats on the board. These boats will have the following lengths:

<ul>

 <li>2 boats of length 5</li>

 <li>2 boats of length 4</li>

 <li>4 boats of length 3</li>

 <li>2 boat of length 2</li>

</ul>

The user should be told how many boats are on the board when the game begins.

Hint: To randomly place a boat, consider the coordinate in the upper left. If the upper left corner was (0<em>,</em>0), consider how the boat looks if it is horizontal or vertical. What upper left corner coordinates are invalid? The placing of the boats may be the most challenging aspect of this project: see what assumptions you can make to simplify it.

Hint: To generate random numbers, the Math.random() method can be used. However, this method returns a double in the range 0 to 1. We will need to scale this and then round it to a whole. To do this, use the Math.floor(x) function, which takes a double x and rounds it down to the nearest integer. For example, Math.floor(2.9) is 2.

<ol start="3">

 <li>TURNS</li>

</ol>

<h1>3       Turns</h1>

Each turn, the user will input a location <em>x,y </em>to attack on the board. You can assume that <em>x </em>and <em>y </em>are integers, but you will need to check if the pair <em>x,y </em>is a valid location on the game board later. For this game you can assume that <em>x </em>represents which row to fire on and <em>y </em>is which column to fire on, with the 0th coordinate representing the first column or row. For example, firing on coordinate (1,0) would fire on the spot in the second row and first column.

<ul>

 <li>If there is no boat at the location, print “miss”.</li>

 <li>If the user has already attacked that location or location is out of bounds, print “penalty”.</li>

 <li>If there is a boat, print “hit”. If the boat sinks, print “sunk”. Do not print “hit” again if the user has already “hit” this location.</li>

</ul>

If the user attacks the same spot twice or attacks a spot out of bounds, the user’s next turn will be skipped (meaning that an extra turn will be added to the turn counter. See the example below for clarification). The game ends when all the boats have been sunk. The game should report how many turns it took to sink all the boats, as well as the total number of cannon shots. Lower scores are better!

Example:

Suppose the user is playing on board of size 5×5 with one boat on it. While in the actual game there will be at least 5 boats on the board and a board size of at least 8×8, for this example let’s assume that just one 3-length boat is placed on the board with the coordinates (0<em>,</em>0)<em>,</em>(0<em>,</em>1)<em>,</em>(0<em>,</em>2).

Turn 1: the user selects (1<em>,</em>0) and “miss” is printed

Turn 2: the user selects (0<em>,</em>0) and “hit” is printed

Turn 3: the user selects (0<em>,</em>0) again and is penalized by losing turn 4. “penalty” is printed

Turn 4: skipped

Turn 5: the user selects (0<em>,</em>1) and “hit” is printed

Turn 6: The user selects (−1<em>,</em>0) which is out of bounds. Penalty

Turn 7: skipped

Turn 8: the user selects (0<em>,</em>2) and “sunk” is printed. The game ends because the last boat has sunk

The total number of turns is 8, but the total number of cannon shots is only 6 (Turns 1, 2, 3, 5, 6, 8).

Before each turn, a visual representation of the current board should be printed to the screen. This allows the player to see which squares they have seen (meaning have fired on), while still obscuring the squares they have not. Printing the board involves printing the locations of the current hits and misses, as well as any locations that have been scanned by the drone. You can format output as a grid, or simply provide a list of information, but it should be easy to understand.

<h2>4. POWERS</h2>

<h1>4      Powers</h1>

There are two special powers that you will implement for this project. Each power can be used <strong>once </strong>a game if the game is in <strong>standard </strong>mode, and <strong>twice </strong>if the game is in <strong>expert </strong>mode. Each power will add one turn to the total turn count, but will not count as a shot fired. If the user attempts to use the power again a message will be printed notifying them that they have already used that power as many times as they can. There is no turn penalty for trying to use a power when you have already hit the limit.

<h1><strong>Drone</strong></h1>

At any point in the game, once the board is initialized and the mode has been chosen, the user can type in ”drone” (or whatever way you want them to signify to the program that they wish to use a drone).

The program will then ask the user if they want to scan a row or column. The user will respond, for example by typing in ”row”. If the user types in an invalid response, the program should alert them until they type in a valid response.

Next, the program will ask the user which row or column they wish to scan. The user will respond by typing in a number, for example 0. If the user types in a number that is out of boundaries, the program should alert them until they type in a valid number.

The program will then ”scan” that row or column, and determine how many spots are there that contain a boat. It will then print that information out to the user. For example in the above

<h2>4. POWERS</h2>

example where a user entered ”row” and 0, the program would scan the 0th (or first row) and return the number of boat spots in that row. The drone will count boat spots that have already been hit and sunk.

Note: The above example is just a potential way that the drone would work during a game. However you wish to have the drone interaction work is fine, as long as it is clear what commands a user has to enter to select the necessary arguments, as well as call the drone.

<h1><strong>Missile</strong></h1>

At any point in the game, once the board is initialized and the mode has been chosen, the user can type in ”missile” (or whatever way you want them to signify to the program that they wish to use a missile).

The program will then ask the user for a coordinate. The user will type in two numbers (Example: 0 5). The program will then check if the coordinate (0,5) is valid for the board. If it is not, the program will continue to ask the user to type in valid coordinates until the user does so.

Next, the program will fire a missile in that spot, what that means is that it will fire at a 3×3 square, with the chosen spot being in the very center of the square. If the chosen spot is near the edge of the board, the missile will only hit the spots on the board.

In the above case, a missile will launch at coordinates (2,2). This will hit spots (1,1),(1,2),(1,3),(2,1),(2,2),

<h2>5. STANDARD AND EXPERT GAME MODES</h2>

(2,3),(3,1),(3,2), and (3,3).

Another example is if a user launches a missile at coordinates (0,0). In this case, because (0,0) is near the edge of the board, only the spots that are on the board will be hit. In this case spots (0,0) (0,1),(1,0) and (1,1) will be hit. Note: It is fine if the spot to launch the missile has already been fired upon, or even if all the spots the missile will be hit have already been fired upon. The only invalid missile use is firing outside of the board.

<h2>5           Standard and Expert Game Modes</h2>

At the beginning of the program, the terminal should prompt the user if they want to play the game in standard of expert mode.

To recap the differences between Standard and Expert Mode.

<strong>Standard Mode:</strong>