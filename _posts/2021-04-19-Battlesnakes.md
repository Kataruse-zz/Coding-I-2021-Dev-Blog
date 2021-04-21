---
title: "Battlesnake Reflection"
Date: 2021-04-19
---

<h2><b>Introduction/b></h2>
Two weeks ago we were tasked with working in a two person team to make a Battlesnake to compete in a class tournament. We were givin some starter code but we had to code the snake to not run into itself or others.

<h2><b>Coding the snake</b></h2>
We Started off by brainstorming how to tackle this problem because there are alot of things to worry about, You have the issue of your snake moving back into its own body, getting food to keep your health up, and avoiding other battlesnakes. Me and my teammate decided the best way to start was to get the snake to not run into itself but we had to break that down into smaller problems to solve it. Heres how we broke it down,
*Determine the snakes direction
--*This will allow us to determine the moves we should remove and can help us with later issues
*Determine the snakes body location
--*We can use the values we get from the snakes body to know what spots to not allow the snake to go to
We first tackled the issue of finding out the direction the snake is facing by first naming the directions the snake could be facing

```javascript
var direction = ['east', 'west', 'north', 'south']
```

We then checked to see if the snakes head X/Y was increasing by one or decreasing by one to find out what direction the snake was moving in, we also made it so that the snake won't go in the opposite direction its facing in because that will always result in a death.

```javascript
//this is on a different document then the code below it
if (!moves.facingEast(head.x, body[1].x)) {
      possibleMoves = possibleMoves.filter(move => move != 'left')
      direction = 'east'
    }
    if (!moves.facingWest(head.x, body[1].x)) {
      possibleMoves = possibleMoves.filter(move => move != 'right')
      direction = 'west'
    }
    if (!moves.facingNorth(head.y, body[1].y)) {
      possibleMoves = possibleMoves.filter(move => move != 'down')
      direction = 'north'
    }
    if (!moves.facingSouth(head.y, body[1].y)) {
      possibleMoves = possibleMoves.filter(move => move != 'up')
      direction = 'south'
    }

    //this is on a different document then the code above it
    facingEast: (headX, bodyX) => {
    if (headX - 1 == bodyX) {
      return false;
    }
    return true;
  },
  facingWest: (headX, bodyX) => {
    if (headX + 1 == bodyX) {
      return false;
    }
    return true;
  },
  facingNorth: (headY, bodyY) => {
    if (headY - 1 == bodyY) {
      return false;
    }
    return true;
  },
  facingSouth: (headY, bodyY) => {
    if (headY + 1 == bodyY) {
      return false;
    }
    return true;
  }
```

While working I worked on defining the directions Eli worked on making sure the snake wouldn't run into the walls of the board. He did this by checking to make sure the head's X & Y cords wouldn't be equal to the boards max or min values.

```javascript
//this code is on a different document from the code below
if (!moves.canMoveUp(height, head.y)) {
      possibleMoves = possibleMoves.filter(move => move != 'up')
    }
    if (!moves.canMoveDown(height, head.y)) {
      possibleMoves = possibleMoves.filter(move => move != 'down')
    }
    if (!moves.canMoveLeft(width, head.x)) {
      possibleMoves = possibleMoves.filter(move => move != 'left')
    }
    if (!moves.canMoveRight(width, head.x)) {
      possibleMoves = possibleMoves.filter(move => move != 'right')
    }

//this code is on a different document from the code above
canMoveUp: (boardHeight, snakeY) => {
    if (snakeY == boardHeight - 1) {
      return false;
    }
    return true;
  },
  canMoveDown: (boardHeight, snakeY) => {
    if (snakeY == 0) {
      return false;
    }
    return true;
  },
  canMoveLeft: (boardWidth, snakeX) => {
    if (snakeX == 0) {
      return false;
    }
    return true;
  },
  canMoveRight: (boardWidth, snakeX) => {
    if (snakeX == boardWidth - 1) {
      return false;
    }
    return true;
  },
```

Now with the directions defined and the snake not being able to move in the opposite direction its facing we decided to next work on avoiding our own body since getting food wasn't that big of a issue and running into the opponents snake wasn't as important as running into ourselves. Again we broke the problem down
*Determine the length of our snake
--*Knowing our snakes lenght will let us run the code to check every body part of our snake
*Determine the X & Y of every body part.
--*If we now the x and y of every body part we can make sure the head doesn't equal it ever.
To get the snake to avoid the body we made it check the X & Y of the first value of the body (which is the head) against the X & Y of every other body part to find out what moves to remove.

```javascript
//this code is on a different document from the code below
possibleMoves = moves.avoidSnakes(body, possibleMoves

//this code is on a different document from the code above
avoidSnakes: (body, possibleMoves) => {
    var head = body[0];
    for (var i = 1; i < body.length; i++) {
      if (head.x + 1 == body[i].x && head.y == body[i].y) {
        possibleMoves = possibleMoves.filter(move => move != "right")
      } else if (head.x - 1 == body[i].x && head.y == body[i].y) {
        possibleMoves = possibleMoves.filter(move => move != "left")
      } else if (head.y + 1 == body[i].y && head.x == body[i].x) {
        possibleMoves = possibleMoves.filter(move => move != "up")
      } else if (head.y - 1 == body[i].y && head.x == body[i].x) {
        possibleMoves = possibleMoves.filter(move => move != "down")
      }
    }
    return possibleMoves;
  },
```