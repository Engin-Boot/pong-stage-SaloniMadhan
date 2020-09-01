# Interaction Sequences

## Startup Sequence

-StartNewGame module sets game level,length of vertical,horizontal walls.
-StartNewGame module calls Paddle controller to set initial paddle coordinates.
-StartNewGame module calls BallController to set radius and initial ball coordinates.
-StartNewGame module calls Player module to initialise score,ballsMissedCount.

## Movement Initiation

-BallController moves the ball towards Player's vertical wall by updating its x,y coordinates. 
-BallController calls CollisionController If Ball hits horizontal/vertical walls/paddle
-CollisionController changes the ball direction by changing current x,y 
coordinates of ball to move it towards nearest vertical wall if ball hits horizontal walls
-CollisionController calls  BallController to update the ball's x,y coordinates for ball's movement. 
-CollisionController calls BallController to resetball position if ball hits vertical wall.
-CollisionController changes the direction by changing current x,y coordinates of ball 
to move it towards opposite vertical wall if ball hits the paddle
-CollisionController calls BallController to update the ball's x,y coordinates for ball's movement.
-In this way,the ball movement repeats on Board till ballsMissedCount of any player is 3.

## One score

-CollisionController calls Player module to increment Player2 score by 5 and 
ballsMissedCount by 1 if ball misses Player1 paddle and hits Player1 vertical wall.
-CollisionController calls Player module to increment the Player1 score by 5 and 
ballsMissedCount by 1 if ball misses Player2 paddle and hits Player2 vertical wall.
-Player module calls Scoreboard to display scores and ballsMissedCount of both players.
-ScoreBoard calls BallController to reset ball position if there is an update in ballsMissedCount or Score.
-Player module calls Scoreboard to declare winner/tie if ballsMissedCount for any player is 3.
