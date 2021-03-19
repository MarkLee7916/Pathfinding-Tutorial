## What is this?

In this tutorial I'll explain the concepts that my visualiser uses. It covers pathfinding algorithms, heuristics, and basic graph theory.

## What is a pathfinding algorithm?

A pathfinding algorithm is an algorithm that tries to find a path between two points. In a CS class we'd think of the algorithms operating on a network of objects and connections between objects, but 
this tutorial will use a 2D grid. Note that no matter what system we use the algorithms are the same, it's just a different way of thinking about it.

## Setup

A pathfinding algorithm only knows a few things. It knows what tile it starts at, what tiles it has visited, and what tiles are adjacent to the ones it's visited. It also knows the goal
if it visits it, but it doesn't know where the goal is. The name of the game is to progressively explore the tiles around it until it eventually reaches the goal. When it visits a tile
it keeps track of what tile it went through to get to it. This allows it to keep track of the path, and display it when it reaches the goal.

## Good algorithms vs Bad Algorithms

The difference between a good algorithm and a bad algorithm depends on the specific problem, but generally we're looking for two things. How fast does it find the path, and
does it find the shortest path? The algorithm we use depends on the answer to these questions. For instance, say we want to find a route from the gym to our home. It's probably
a good idea to find the shortest path so that we don't waste time travelling. However say we just want to verify whether a path exists, then it doesn't matter if the path we use to
verify is the shortest one.

## Uninformed Search

With this setup we can't make a very clever algorithm, but we can still find any existing path and even guarantee that it's the shortest. The idea is to just to explore the grid until we 
hit the goal. When we explore the grid, how do we decide what tile to go to next? This question is the difference between so called "uninformed search algorithms", although I prefer to 
call them exploration algorithms

## Depth First Search

One approach is to always go to the tile we seen most recently. We use a stack (like a stack of papers) to keep track of what tiles we've seen but not searched yet. We repeat the process
until we eventually hit the goal

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
