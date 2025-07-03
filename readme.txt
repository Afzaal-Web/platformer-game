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

Step 21
The next step is to create an update() method which will be responsible for updating the player's position and velocity as it moves throughout the game.
Below your draw() method, create an empty update() method.

Step 22
Inside the update() method, call the draw() method to ensure that the player is continually drawn on the screen as the game updates.
Don't forget to include the this keyword.

Step 23
When the player moves to the right, you will need to adjust its velocity.
Use the addition assignment operator to add the velocity's x coordinate to the player's x position.
Don't forget to include the this keyword for the velocity and position.

Step 24
When the player jumps up, you will need to add the logic for adjusting its velocity.
Use the addition assignment operator to add the velocity's y coordinate to the player's y position.
Don't forget to include the this keyword for the velocity and position.

Step 25
Right now, when the player jumps up, it is possible for it to move past the height of the canvas.
To fix that, you will need to add a condition to stop the player from falling past the height of the canvas.
Create an empty if statement that checks if the sum of the player's y position, height, and y velocity is less than or equal to the height of the canvas.

Step 26
In the if statement, add another if statement to check if the player's y position is less than 0.

Step 27
Inside the inner if statement, assign 0 to the player's y position.

Step 28
Below the this.position.y = 0, assign gravity to the velocity's y position.

Step 29
Below your inner if statement, use the addition assignment operator to add gravity to the y velocity.

Step 30
Add an else clause that assigns 0 to this.velocity.y.

Step 31Passed
The final condition you need to add inside the Player class is to ensure that the player stays within the boundaries of the canvas screen and doesn't move too far off to the left.
Create an if statement, to check if the player's x position is less than the width.

Step 32
Inside the if statement, assign the width to the player's x position.

Step 33
For the last condition, you will need to check if the player's x position has exceeded the right edge of the canvas. If it has, you will need to set the player's x position to the maximum value so the player does not accidentally go off screen to the right.
Inside your update method, create an if statement that checks if this.position.x >= canvas.width - this.width * 2.

Step 34
Inside your if statement, assign canvas.width - this.width * 2 to this.position.x.
This will ensure that the player's x position will never exceed the right edge of the canvas.

Step 35
The next step is to use the new keyword to create a new instance of the Player object and assign it to a new const variable called player.

Step 36
Now it is time to see your new player drawn on the screen.
Start by creating an empty arrow function called startGame.

Step 37
Inside your startGame function, you will need to display the canvas element and hide the startScreen container.
Use canvas.style.display to change the display value to "block".
Below that, use startScreen.style.display to change the display value to "none".

Step 38
To visualize the player on the screen, you need to draw it on the canvas.
Inside the startGame function, call the .draw() method of your player object.

Step 39
Now it's time to add the functionality for the start game button.
Add an addEventListener to the startBtn and pass in a click event and a reference to the startGame function.
Click on the start game button, and you should see a light blue square on the screen which represents the main player.

Step 40
Now that you can see the player on the screen, it is time to start adding the functionality for moving the player across the screen.
Create a new empty arrow function called animate.

Step 41
The requestAnimationFrame() web API, takes in a callback and is used to update the animation on the screen. The animate function will be responsible for updating the player's position and continually drawing it on the canvas.
Inside the animate function, call the requestAnimationFrame() API and pass animate as the argument.

Step 42
As the player moves through the game, you will need to clear the canvas before rendering the next frame of the animation.
You can use the clearRect() Web API to accomplish this. It takes in an x, y, width, and height arguments.
Below your requestAnimationFrame, call the clearRect() method on the ctx variable and pass in 0, 0, canvas.width, canvas.height as the arguments.

Step 43
The next step is to update the player's position as it moves throughout the game.
Below your ctx.clearRect(), call the update() method on the player.

Step 44
To manage the player's movement in the game, you will need to monitor when the left and right arrow keys are pressed.
Create a new const variable called keys and assign it an empty object.

Step 45
Inside the keys object, add a new key called rightKey and assign it an object with the key-value pair of pressed: false.
Below the rightKey object, create a leftKey object and assign it an object with the key-value pair of pressed: false.

Step 46
The next step is to add the logic for increasing or decreasing a player's velocity based on if they move to the left or right of the screen.
Inside the animate function, create an if statement where the condition checks if the right key was pressed and the player's x position is less than proportionalSize(400).
You need to use the proportionalSize function here to make sure the player's x position is always proportional to the screen size.

Step 47
Inside the if statement, assign the number 5 to the player's x velocity.

Step 48
Add an else if statement where the condition checks if the left key was pressed and the player's x position is greater than proportionalSize(100). You need to use the proportionalSize function here to make sure the player's x position is always proportional to the screen size.
Inside the else if statement, assign the number -5 to the player's x velocity.

Step 49
Add an else clause that assigns the number 0 to the player's x velocity.

Step 50
The next step is to add the functionality that will be responsible for moving the player across the screen.
Create a new arrow function called movePlayer that has three parameters called key, xVelocity, isPressed.

Step 51
In the game, the player will interact with different checkpoints. If the isCheckpointCollisionDetectionActive is false, then you will need to stop the player's movements on the x and y axes.
Start by creating an if statement where the condition checks if the isCheckpointCollisionDetectionActive is false.
Remember that you can use the ! operator to check if the variable is false.

Step 52
Inside the if statement, set the player's x velocity to 0 and the player's y velocity to 0.
Below that, add a return statement.

Step 53
Below the if statement, create a switch statement with a value of key.

Step 54
The first case you will want to add is when the left arrow key is pressed.
Inside the switch statement, add a new case called "ArrowLeft".

Step 55
Inside the case clause, assign isPressed to keys.leftKey.pressed.
Below that, add an if statement that checks if xVelocity is equal to 0. If so, assign the xVelocity to player.velocity.x.

Step 56
Below your if statement, use the subtraction assignment operator to subtract the xVelocity from player.velocity.x.
To close out this case, make sure to add a break statement.

Step 57
The player can jump up by using the up arrow key or the spacebar.
Add three new cases for "ArrowUp", " ", and "Spacebar". Remember that you can group cases together when they share the same operation.
Inside those cases, use the subtraction assignment operator to subtract 8 from player.velocity.y.
To close out these cases, make sure to add a break statement.

Step 58
The last case you will need to add will be for "ArrowRight".
Inside that case, assign isPressed to keys.rightKey.pressed.
Add an if statement that checks if xVelocity is equal to 0. If so, assign the xVelocity to player.velocity.x.
Below that if statement, use the addition assignment operator to assign the xVelocity to player.velocity.x.

Step 59
Now it is time to add the event listeners that will be responsible for calling the movePlayer function.
Start by adding an addEventListener to the global window object.
For the arguments, pass in the keydown event and an arrow function that uses the destructuring assignment to get the key property from the event object in the event listener parameter.
Here is the syntax for using the destructuring assignment in the parameter list of the arrow function:
Example Code
btn.addEventListener('click', ({ target }) => {
  console.log(target);
});

Step 60
Inside the arrow function, call the movePlayer function and pass in key, 8, and true as arguments.

Step 61
Add another addEventListener to the global window object and pass in the keyup event and use destructuring to pass in the key property from the event.

Step 62
Inside the callback function, call the movePlayer function and pass in key, 0, and false as arguments.

Step 63
Before you can start moving your player across the screen, you will need to use the animate function.
Inside the startGame function, delete player.draw() and call the animate function.
Click the Start Game button and use the left and right arrow keys to move the player across the screen. You can also use the spacebar or the up arrow key to jump up.

Step 64
The next step is to create the platforms and platform logic.
Start by creating a new Platform class.

Step 65
Inside the Platform class, create a constructor that takes in the x and y coordinates.

Step 66
When working with objects where the property name and value are the same, you can use the shorthand property name syntax. This syntax allows you to omit the property value if it is the same as the property name.
Example Code
// using shorthand property name syntax
obj = {
  a, b, c
}
The following code is the same as:
Example Code
obj = {
  a: a,
  b: b,
  c: c
}
Inside the constructor, add this.position and assign it an object with the x and y coordinates. Make sure to use the shorthand property syntax .

Step 67
Next, add a width property to the constructor and assign it the number 200.
Don't forget to use the this keyword to access the properties.

Step 68
Below that, add a height property and assign it the number proportionalSize(40). You need to use the proportionalSize() function to make sure the height is proportional to the screen size.
Remember to use the this keyword to access the properties.

Step 69
Next, add a draw method to the Platform class.

Step 70
Inside the draw method, assign "#acd157" to the ctx.fillStyle.
Below that, call the ctx.fillRect method and pass in the x and y coordinates, along with the width and height properties. Remember to include this before each property.