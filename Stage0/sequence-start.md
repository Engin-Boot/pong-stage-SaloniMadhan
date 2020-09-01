# Interaction Sequences

## Startup Sequence

-StartNewGame module sets game level,board bg color,length of vertical,horizontal walls.
-StartNewGame module calls Paddle controller to set initial paddle coordinates.
-StartNewGame module calls BallController to set radius and initial ball coordinates.
-StartNewGame module calls Player module to initialise score and ballsMissedCount to 0.

## Movement Initiation

-BallController moves the ball towards Player's vertical wall by 
updating its x,y coordinates from initial ball position. 
-BallController calls CollisionController If Ball hits horizontal or vertical walls or paddle
-CollisionController changes the ball direction by changing current x,y 
coordinates of ball to move it towards nearest vertical wall if ball 
hits horizontal walls,calls  BallController to update the ball's 
x,y coordinates for ball's movement. 
-CollisionController calls BallController to resetball position if ball hits vertical wall and misses the paddle.
-CollisionController changes the direction by changing current x,y coordinates of ball to move it towards opposite vertical wall if ball hits the paddle,calls BallController to update the ball's x,y coordinates for ball's movement.
-In this way,the ball movement repeats on the playBoard till ballsMissedCount of any one player is equal to 3.

## One score

-CollisionController calls Player module to increment the Player 2 score by 5 and 
ballsMissedCount by 1 if ball misses Player 1 paddle and hits Player 1 vertical wall.
-CollisionController calls Player module to increment the Player 1 score by 5 and 
ballsMissedCount by 1 if ball misses Player 2 paddle and hits Player 2 vertical wall.
-Player module calls Scoreboard to display scores and ballsMissedCount of both players.
-ScoreBoard calls BallController to reset ball position to original position if there is an update in ballsMissedCount or Score.
-Player module calls Scoreboard to declare winner or tie if ballsMissedCount for any player becomes equal to 3.
