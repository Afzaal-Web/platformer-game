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
As you are designing the game, you will need to make sure that the size of the elements in the game are responsive and adapt to different screen sizes.
Start by creating an arrow function called proportionalSize that takes in a size parameter.

Step 11
The width and the height of the main player, platforms and checkpoints will be proportional sized relative to the innerHeight of the browser screen. The goal is to make the game responsive and visually consistent across different screen sizes.
Inside your proportionalSize function, you will need to return a ternary that checks if innerHeight is less than 500. If so, return Math.ceil((size / 500) * innerHeight), otherwise return size.

Step 12
The next step is to define some characteristics for the main player of the game.
Start by creating a new class called Player.

Step 13
Inside your Player class, you will need to define the player's position, velocity, width, and height values. All of these values will be defined inside the constructor method.
Create an empty constructor inside your Player class.

Step 14
Inside your constructor, use the this keyword to set the position property to an empty object.

Step 15
Inside your position object, add a new key called x with a value of proportionalSize(10). After that, add another key called y with a value of proportionalSize(400).
You need to use the proportionalSize function here to make sure that the player's position is always proportional to the screen size. This is important because you want the player to be able to move around the screen regardless of the screen size.

Step 16
Below your position object, use the this keyword to set the velocity property to an object.
Inside that new velocity object, create a key called x with a value of 0 and a new key called y with a value of 0.
The velocity property will be used to store the player's speed in the x and y directions.

Step 17
Below your velocity object, use the this keyword to set the width property to proportionalSize(40).
Below your width property, use the this keyword to set the height property to proportionalSize(40).
You are using the proportionalSize() function here to set the width and height properties of your class to be proportional to the height of the screen.

Step 18
The next step is to create a draw() method, which will be responsible for creating the player's width, height, position, and fill color.
Below your constructor, create an empty draw() method.

Step 19
Now, you need to set the color for your player.
Inside the draw() method, assign the string "#99c9ff" to ctx.fillStyle.

Step 20
Below your ctx.fillStyle, you need to create the player's shape by calling the fillRect() method on the ctx object which you instantiated earlier.
Example Code
fillRect(x, y, width, height)
Inside the fillRect() method add the this.position.x, this.position.y, this.width and this.height values.

