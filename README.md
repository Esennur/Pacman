# search

Search Project

Search.py

Depth-first search function:
Utilizes util.Stack() to visit coordinates in a depth-first search manner
In order to keep track of the “right” path to the goal, keeps states like this:
currState = (firstState, [])
This way it can access the coordinates of the position and the path that it took from the start position to that position
This functionality is crucial as keeping track of the right path and returning it is even hard with backtracking (tried it).
Bread-first search function:
Utilizes util.Queue() to visit coordinates in a bread-first search manner
It stores the path and position together just like depth-first search
Keeps track of the visited nodes with a list because using a set caused “unhashable type: list” problems in Q5 tests
Uniform cost search:
Utilizes util.PriorityQueue() to visit coordinates in a priority-based manner
Unlike other methods it uses a directory to keep track of each state’s path and distance
Same map is used for checking whether a coordinate was visited before
A star search:
It works the same as Uniform cost search except it uses a heuristic function which is gotten as a parameter and in order to prioritize successor coordinates it uses the formula: “distance so far + cost of the action + heuristics(position)”



SearchAgents.py

CornersProblem:

The hardest part of implementing this was deciding on how to keep track of the visited corners without needing to change functions in search.py. In order to accomplish that I decided to store the states as (state, visitedCornersList). You can see it in getStartState() method.
Doing so allowed me to keep track of what corners are visited without breaking the path. 
IsGoalState() 
has two different returning ways the first one is the one Q5 uses. And the second one is used by Q6. Since Q6 hasn’t got problems of breaking the path and not returning the right path, the second one was enough for it. However, for Q5, simply checking if the corners were visited or not in general didn’t generate the right path. Because what I had to check for was if the current path is passing all the corners or not. Which was possible thanks to my decision of keeping states as tuples with the coordinate and corners list. 
GetSuccessors()
Returns the successors of the given state in a tuple.
Crucial for making Q5 work. 
It adds the successors into their corner list if they are a corner, therefore adding corners to the according lists without modifying search.py code
CornersHeuristic()
Utilizes util.ManhattenDistance() method to find the given state’s minimum distance to any of the corners
FoodHeuristic()
Utilizes MazeDistance() method in searchAgents.py to find the maximum distance of the given state to any of the foods in the foodlist


