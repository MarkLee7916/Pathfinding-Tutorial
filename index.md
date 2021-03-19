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
call them exploration algorithms

## Depth First Search

One approach is to always go to the tile we seen most recently. We use a stack (like a stack of papers) to keep track of what tiles we've seen but not searched yet. We repeat the process
until we eventually hit the goal. This won't find the shortest path, but it will find any path if it exists.

## Breadth First Search

Another approach is to always go to the tile we seen least recently. We use a queue (like a queue outside a shop) to keep track of what tiles we've seen but not searched yet. We repeat the process
until we eventually hit the goal. This guarantees the shortest path, but why?

When we explore, we start by adding all adjacent tiles to the starting tile into the queue. These tiles are all a distance 1 from the starting tile. When we visit the next tile, we add all of its
adjacents onto the queue, which are a distance 2 from the starting tile. Since this is a queue, we explore all the tiles we seen least recently. Since the tiles at distance 1 were added first,
we'll get through all the tiles at distance 1 before we consider any tile at distance 2. This idea continues throughout the algorithm; we'll consider the tiles at distance 2 before we consider the tiles
at distance 3 and so on...

When we visit the goal we know we've found the shortest way to get to it, because if a shorter way existed we'd have seen it before. Say the goal was at distance 10. We've already explored all the tiles
at distances 1 through 9, and none of them were the goal, so we know for sure that the way we've got to the goal is the minimum distance, which means that it must also be the shortest path

## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/MarkLee7916/Pathfinding-Tutorial/edit/gh-pages/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/MarkLee7916/Pathfinding-Tutorial/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out.
