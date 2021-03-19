## What is this?

In this tutorial I'll explain the concepts that my visualiser uses. It covers pathfinding algorithms, heuristics, and very basic graph theory.

## What is a pathfinding algorithm?

A pathfinding algorithm is an algorithm that tries to find a path between two points. In a CS class we'd think of the algorithms operating on a network of objects and connections between objects, but 
this tutorial will use a 2D grid. Note that no matter what system we use the algorithms are the same, it's just a different way of thinking about it.

## Applications

Whenever we need to find a path between any two points automatically (i.e google maps, finding a route in a video game) we'll use a pathfinding algorithm. However, they also have
a lot of applications that aren't obvious at first glance. For instance, we can use them to solve rubix cubes by treating all the possible configurations of the cubes as 
points, and connections between any cubes that can be moved between by turning the cube. This forms a network, which can be explored using pathfinding algorithms. The path we get back
can be used as a series of steps needed to solve the cube.

## Setup

A pathfinding algorithm only knows a few things. It knows what tile it starts at, what tiles it has visited, and what tiles are adjacent to the ones it's visited. It also knows the goal
if it visits it, but it doesn't know where the goal is. The name of the game is to progressively explore the tiles around it until it eventually reaches the goal. When it visits a tile
it keeps track of what tile it went through to get to it. This allows it to keep track of the path, and display it when it reaches the goal.

## Good algorithms vs Bad Algorithms

The difference between a good algorithm and a bad algorithm depends on the specific problem, but generally we're looking for two things. How fast does it find the path?, and
does it find the shortest path? The algorithm we use depends on the answer to these questions. For instance, say we want to find a route from the gym to our home. It's probably
a good idea to find the shortest path so that we don't waste time travelling. However say we just want to verify whether a path exists, then it doesn't matter if the path we use to
verify is the shortest one.

## Uninformed Search

With this setup we can't make a very clever algorithm, but we can still find any existing path and even guarantee that it's the shortest. The idea is to just to explore the grid until we 
hit the goal. When we explore the grid, how do we decide what tile to go to next? This question is the difference between so called "uninformed search algorithms", although I prefer to 
call them exploration algorithms.

## Depth First Search

One approach is to always go to the tile we seen most recently. We use a stack (like a stack of papers) to keep track of what tiles we've seen but not searched yet. We repeat the process
until we eventually hit the goal. This won't find the shortest path, but it will find any path if it exists.

## Breadth First Search

Another approach is to always go to the tile we seen least recently. We use a queue (like a queue outside a shop) to keep track of what tiles we've seen but not searched yet. We repeat the process
until we eventually hit the goal. This guarantees the shortest path, but why?

When we explore, we start by adding all adjacent tiles to the starting tile into the queue. These tiles are all one tile away from the starting tile. When we visit the next tile, we add all of its
adjacents onto the queue, which are two tiles away from the starting tile. Since this is a queue, we explore all the tiles we seen least recently. Since the tiles that were one away were added first,
we'll get through all the tiles at that are one away before we consider any tile two tiles away from the starting tile. This idea continues throughout the algorithm; we'll consider the tiles that are two away before we consider the tiles
at three away and so on...

When we visit the goal we know we've found the shortest way to get to it, because if a shorter way existed we'd have seen it before. Say the goal was 10 tiles away from the starting tile. We've already explored all the tiles
at distances that are within 9 tiles away, and none of them were the goal, so we know for sure that the way we've got to the goal is the minimum distance, which means that it must also be the shortest path.

## Weights

When you're exploring the world not all roads are created equal. Some are smooth and easy to drive on, while some are bumpy and full of potholes. So what seems like the shortest path might not actually be the shortest path if we have to cross a bunch
of badly paved roads. To model this, we can assign a tile a weight which tells us how much it costs to cross it. To find the shortest path, some algorithms will try to minimise the total cost. Algorithms that do this are weighted.
However some algorithms simply ignore these weights. These algorithms are unweighted.
            
## Dijkstra's algorithm

Breadth first search and depth first search don't consider these weights, so we need a new algorithm, namely Dijkstra's. The idea behind Dijkstra's is to keep track of the total
cost to get to each tile as we explore the grid. For instance if to get to a tile we had to get through tiles of weights 1, 2, and 3, then the total cost would be 6.
When it comes to selecting which tile to visit next, we always pick the tile with the lowest total cost. This guarantees the shortest path for weighted grids, but why?

The reasoning is similar to breadth first search. Since we always look at nodes that are the smallest cost, we know that when we reach the goal there can't have been a shorter
path to the goal, as we would have already seen it before.

## Informed Search

You may be wondering, what if we actually know where the goal is? For instance in a grid what if we could say for sure "the goal is in position (10, 10)"? We don't necessarily 
know how to get to the goal, but we know what direction we should be looking in at least. This leads us to two new algorithms. One algorithm guarantees the shortest path, and does it
faster than Dijkstra's, while one finds us a path rapidly, but not necessarily the shortest one.

## Best First Search

Since this is a coordinate system, we can estimate the distance from the goal if we know what coordinate the goal is in. For instance if we're at the coordinate (5, 5) and the
goal is at (10, 10) then we can estimate the distance from the goal to be a total of 10 steps. Note that this is just an estimate. There could be obstacles that prevent
us from actually getting there in 10 steps, but it still helps us move in the right direction. This leads to an algorithm called best first search. The idea
is to always pick the tile with the smallest estimated distance to the goal. This gets us to the goal quickly because we won't waste time searching in the wrong direction.

## A*

A* allows us to use the estimated distance from the goal to find a path quickly, but always guarantees the shortest path. On top of that
it also works for weighted graphs. The idea is to always pick the tile that has the minimum value of

`total cost to get to here from start + estimated distance from here to goal`

We can see why this will help us reach the goal faster. If a tile is far away from the goal, A* is less likely to pick it as the estimated distance is a factor in how it picks
which tile to explore next. However, it's not so obvious why this will give us the shortest path. In fact, A* will only guarantee the shortest path if our estimate never overestimates the distance.
But why?








                
            
