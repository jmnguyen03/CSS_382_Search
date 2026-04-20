Q1: Depth First Search (DFS)
I implemented DFS as a graph search using a Stack for the fringe. By keeping track of a visited set, the algorithm avoids getting stuck in infinite loops in cyclic mazes. It explores the deepest nodes first, which works, but as expected, it doesn't always find the shortest path.

Q2: Breadth First Search (BFS)
For BFS, I swapped the data structure to a Queue. This ensures the algorithm explores nodes layer-by-layer. Since it hits the shallowest goal state first, it successfully finds the least-cost solution in terms of the number of actions.

Q3: Uniform Cost Search (UCS)
I used a PriorityQueue for UCS to account for different step costs. The priority is based on the total cumulative cost to reach a node. This allows Pacman to stay east or west depending on the specific cost function being passed in, always finding the mathematically "cheapest" path.

Q4: A Search*
A* was implemented using a PriorityQueue where the priority is $f(n) = g(n) + h(n)$. By combining the actual cost from the start ($g$) with a heuristic estimate to the goal ($h$), the agent finds the optimal path while expanding significantly fewer nodes than UCS.

Q5: Corners Problem
The state space for this problem was defined as a tuple containing Pacman's current $(x, y)$ coordinates and a second tuple of four booleans tracking which corners have been visited. The successor function updates these booleans when Pacman "touches" a corner, and the goal is reached only when all four are True.

Q6: Corners Heuristic
My heuristic calculates the Manhattan distance from the current position to the furthest unvisited corner. This is admissible because Pacman must travel at least that far to finish the problem. It’s also consistent because moving one step can only reduce the distance to that furthest corner by at most one.

Q7: Food Heuristic
For the food-clearing problem, I implemented a heuristic that finds the maze distance to the single furthest food dot remaining on the map. This provides a strong lower bound on the actual remaining cost, helping A* stay efficient even in tricky layouts.

Q8: Suboptimal Search
I implemented the goal test for AnyFoodSearchProblem to return True as soon as Pacman lands on any coordinate containing food. The findPathToClosestDot function then uses BFS to find the shortest path to the nearest dot. While this is greedy and might not be optimal for the whole maze, it's very fast.