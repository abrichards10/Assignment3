// Angela Richards
/* NOTES:

- you may use Java Swing and Java AWT

On command line, the game is provided with the following parameters, in order:
1. Number of tubes. This number must be at least 3. While there is no theoretical upper limit on
this number, you may assume a practical upper limit of no less than 12.
2. Number of balls per tube. This number must be at least 4. As with the number of tubes, there is
no theoretical upper limit, but you may assume a practical upper limit of 8 or more.
3. Number of filled tubes. This number must be at least 2 and must be no more than (number of
tubes) - 2.

Terminal command: java TowersOfFourOrMore 5 4 2
(produces 5 tubes, 4 balls per tube, with 2 of the tubes filled)

- The number of filled tubes also determines the number of unique colours for the balls
- For each colour, there are “number of balls per tube“ instances.
- The balls are randomly ordered and placed in tubes from left to right, starting with tube 0

Requirement 2: Make moves toward the goal state
The goal state for the game is to have all the blue balls / “1” values in any one of the tubes and all the
brown balls / “0” values in another tube. Once the starting point for the game has been generated as
defined above, the game proceeds to the goal state, with the following rules:
     1. The game may perform only one move at a time.
     2. No tube may exceed its capacity, set by the number of balls per tube parameter.
     3. Only the top ball of a tube may move from its original tube to any other tube which has not
        exceeded its capacity.
     4. A moved ball always moves to the top of the tube to which it is moved.

Requirement 3: Show moves
Once the moves have been determined, show the sequence of moves from start to goal state, in order.
The printing of moves may look like the following, which starts with the movement from one tube (eg. tube
0 = t0) to another tube (eg. tube 2 = t2):
t0 - t2
t1 - t2
t1 - t2
t1 - t2
t0 - t1


 */
