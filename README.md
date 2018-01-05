<h2> CS-251 "Snake Game" Final Project: Part 1 </h2>

<b>**The classes contained within this repository are the work of <i>Pablo Edgar</i> and are for reference only. </b>

<h3>CONTENTS OF THIS FILE</h3>
—————————————————
<ul>
<li>Objects in Game</li>
<li>Description of Project Classes</li>
<li>Algorithm Details</li>
<li>GamePlay and Scoring</li>
<li>Moving the Snake</li>
<li>Food and Snake Growth</li>
<li>Wall and Snake Collisions</li>
<li>Game Maps</li>
</ul>

<h3>INTRODUCTION</h3> 
——————————————————
<br>Part 1 of Final Project for CS 251 - Runs a Snake Game with hard-coded movment values for testing purposes. 
Proceeds to print out a string representation of a gameboard and various snake objects with several test cases 
to show functionality.

In a snake game the objective is to navigate a snake through a walled space
(or maze), consuming food along the way. The user must avoid colliding with walls or the
snake's ever-growing body. The length of the snake increases each time food is consumed.

<h3>REQUIREMENTS</h3>
——————————————————
<br> Wall configuration file - maze-simple.txt and maze-cross.txt included within repository.
<br> tester-transcript.txt displays example output of program 

<h3>GAME INFORMATION</h3>
——————————————————

<h4>OBJECTS IN GAME:</h4>

"Food" = Represented by 'f'<br>
"Snake" = Represented by 's'<br>
"Wall" = Represented by 'x'<br>

<h4>DESCRIPTION OF PROJECT CLASSES:</h4>

<i>Snake.java</i><br>
The Snake class gives the “Snake” movement. Handles logic of snake. Snake is represented by a LinkedList that is manipulated throughout game. Implements FindPoint interface to handle a contains method.

<i>Food.java</i><br>
The Food class creates a Point (X,Y) that is represented as a “Food” object. The snake can “eat” this point. 

<i>Wall.java</i><br>
The Wall class creates boundaries within game that “kill” snake. Use starting and ending values, and (0,0) as top left corner for reference.

<i>Point.java</i><br>
The Point class allows the entire game and its objects to be referenced by (X,Y). Also gives direction to snake during movements (North, South, East, West). Use (0,0) to be top-left corner.

<i>FindPoint.java</i><br>
Common FindPoint interface with contains() method. Implemented in Snake class. Used to check if point contains a specific object.

<i>GameManager.java</i><br>
The GameManager class handles the snake, wall, and food book-keeping. Takes in a text file as a constructor. Handles parsing of text file and conversion of numbers by storing values in a ArrayList to create representation of board. Contains methods that generate food, control snake, and update board state. 

<i>GameManagerTester.java</i><br>
The GameManagerTester class checks Snake game functionality. Loops through hard-coded values to move snake and utilizes methods in GameManager to print out string representation of board and its objects contained within.

<h4>ALGORITHM DETAILS:</h4>

<i>Moving and growing the snake</i><br>
Move snake in particular direction using Direction input (North, South, East, West). Direction is dictated by arrow key events on keyboard. Since board starts at (0,0) in the top left corner, inverse values for North and South (eg. North = (0,-1)). Move snake forward by adding a point to front of snake in current direction, and removing the ‘tail’ by polling the last element in the LinkedList. Check if food object is eaten by seeing if head (snake.peekFirst()) contains a Food at a given instance.  If food object eaten, add a new Point to snake to allow the snake to grow. 

<i>Detecting collisions</i><br>
Iterate through walls on board and check to see if head of snake (snake.peekFirst()) contains a Wall object. Use same logic to check if snake collided with food or with itself. Return a boolean value true/false depending on result. 

<i>Detecting end of game</i><br>
Check status of boolean value returned from detectCollision() method in GameManager. If boolean value from collision with wall or snake is true, the game has ended. 

<i>Printing out game board state</i><br>
Override toString() in GameManager to print out representation of board. Use nested for loops to check each point within width and height boundaries of board, then check each point for specific object (Food, Wall, Snake), and print string representation of these objects. Use a StringBuilder to concatenate strings during board creation to improve program performance. 

<h4>MOVING THE SNAKE:</h4>

The snake movement is dictated by hard-coded values. Movement is not controllable by user for this portion of the lab.

<h4>FOOD AND SNAKE GROWTH:</h4>

A "food" item (represented by a "f) is generated at a random unoccupied location at the start of the game. The location is determined as valid if the point does not contain a "Wall", another "Food", or a "Snake". 

A snake has a original length of 1 segment. If the Snake collides with a food, the snake consumes the food and grows in length by adding 1 segment to the tail. A new food is then generated at a new random valid location.

<h4>WALL AND SNAKE COLLISIONS:</h4>

If a snake collides with a wall or its own body, the game is ended. 

<h4>GAME MAPS:</h4>

Game is preloaded with two trial map configurations for testing.

