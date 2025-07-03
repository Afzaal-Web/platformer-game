Step 1:
Start by using document.getElementById() to get the #start-btn and #canvas elements.

Store them in const variables named startBtn and canvas respectively.

Step 2:
Next, you will need to use document.querySelector to get the .start-screen and .checkpoint-screen elements.

Store them in const variables called startScreen and checkpointScreen respectively.

Step 3:
The next step is to target the paragraph element inside the .checkpoint-screen element.

Use document.querySelector and the child combinator > to target the paragraph element.

Assign that value to a const variable called checkpointMessage.

Step 4:
Before you can begin building out the functionality for the game, you will need to set up the ability to add 2D graphics.
The Canvas API can be used to create graphics in games using JavaScript and the HTML canvas element.
You will need to use the getContext method which will provide the context for where the graphics will be rendered.
Example Code
canvas.getContext("2d");
Assign that getContext method to a const variable called ctx.

Step 5:
The canvas element has a width property which is a positive number that represents the width of the canvas.

Example Code
canvas.width
Below your const declarations, append the width property to the canvas variable.

Step 6:
The innerWidth property is a number that represents the interior width of the browser window.
Assign innerWidth to canvas.width.

Step 7:
The innerHeight property is a number that represents the interior height of the browser window.
Below your canvas.width, append the height property to the canvas variable and assign it innerHeight.

Step 8:
In your platformer game, the main player will need to jump between the different platforms. When the player jumps, you will need to apply gravity to bring them back down.
Create a new const variable called gravity and assign it the number 0.5.

Step 9:
In the game, the player will have the opportunity to cross different checkpoints. You will need to keep track of the status for the checkpoint collision detection.
Use let to create a new variable called isCheckpointCollisionDetectionActive and assign it the value of true.

Step 10:
Step 10
As you are designing the game, you will need to make sure that the size of the elements in the game are responsive and adapt to different screen sizes.
Start by creating an arrow function called proportionalSize that takes in a size parameter.