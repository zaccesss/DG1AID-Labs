# DG1AID - Week 6 Notes
## Unit 3 - Solving Problems by Search (Part I)

---

## Lecture Overview

Week 6 begins Unit 3. It introduces how AI agents solve problems by searching through possible states. Topics covered:

- Agents (goal-based and reflex)
- Problem formulation
- Search trees and state spaces
- Uninformed search: BFS and DFS

---

## Agents

An agent is an AI algorithm that determines optimal actions to reach a desired state.

### Two Types of Agents

**Goal-based agents:**

- Use planning and foresight to select actions that achieve specific long-term objectives
- Think ahead about consequences of actions
- More sophisticated and flexible
- Example: a chess AI that plans several moves ahead

**Reflex agents:**

- Act immediately based on current observable stimuli
- Follow condition-action rules: if this, then do that
- No memory or planning
- Example: a thermostat that turns heating on when temperature drops below a threshold

---

## Problem Formulation

Before searching for a solution, you must formally define the problem. This involves:

1. **Initial State** - where does the agent start? Example: the 8-puzzle starting configuration, a robot at position (0,0)
2. **Actions / Successor Function** - what moves are available in any given state? Example: in the 8-puzzle, slide a tile up, down, left or right
3. **Goal Test** - how do you know when you have reached the goal? Example: the 8-puzzle is solved, the robot has reached position (5,3)
4. **Path Cost** - how expensive is each action? Example: each move costs 1, roads have different distances
5. **Solution** - a sequence of actions from initial state to goal state

### Abstraction

Real problems are too complex to model every detail. Abstraction means simplifying the problem to only the relevant details needed for the search.

Example: a robot navigating a maze. You do not model every atom of the robot or the maze, you just model positions and moves.

### Example Problems

| Problem | State | Actions | Goal |
|---|---|---|---|
| 8-puzzle | Tile configuration | Slide tile | Tiles in correct order |
| Maze | Current position | Move N/S/E/W | Reach exit |
| Route finding | Current city | Drive to adjacent city | Reach destination |
| Tower of Hanoi | Disk configuration | Move top disk | All disks on target peg |
| 8-Queens | Queen positions on board | Place a queen | No two queens attack each other |

---

## Search Trees

A search tree is how we systematically explore all possible states by expanding nodes.

- Each node represents a state
- Each edge represents an action
- The root is the initial state
- Leaf nodes are unexplored states
- A path from root to a node represents a sequence of actions

```text
              A (root, depth 0)
            / | \
           B  C  D        <- depth 1, children of A
          /|      \
         E F       G      <- depth 2
```

### Key Terms

**Frontier (Open List):** the set of nodes that have been generated but not yet expanded. This is what we explore next.

**Explored (Closed List):** the set of nodes already expanded. We avoid revisiting these to prevent infinite loops.

**Branching Factor (b):** the number of actions available from any given state. How many children does each node have?

**Depth (d):** the level of a node in the tree. Root is depth 0.

**Path Cost (g):** the total cost of getting from the root to the current node.

### Repeated States

A critical problem in search: you can visit the same state via different paths. Without tracking visited states you can get infinite loops. Solution: maintain an explored set and never revisit states already expanded.

---

## Evaluating Search Algorithms

Four criteria for evaluating any search algorithm:

| Criterion | Definition | Question |
|---|---|---|
| Completeness | Will it always find a solution if one exists? | Does it always find a solution? |
| Optimality | Does it find the best (lowest cost) solution? | Is the solution the best possible? |
| Time Complexity | How long does it take? | How many nodes are expanded? |
| Space Complexity | How much memory does it use? | How many nodes are stored at once? |

Big O notation is used to express complexity:

- O(b^d) means the time grows exponentially with depth d and branching factor b
- O(b^m) means time grows exponentially with maximum depth m

---

## Uninformed Search

Uninformed search (also called blind search) means the algorithm has no additional information about which states are more promising than others. It explores states in a fixed order without any domain knowledge.

### Breadth-First Search (BFS)

**Strategy:** explore all nodes at depth d before exploring any nodes at depth d+1. Uses a FIFO (First In, First Out) queue, nodes added to the back and removed from the front.

**Visualise it:** level by level, explore all children of the root, then all grandchildren, then all great-grandchildren etc. Using the tree above, BFS visits in the order A, B, C, D, E, F, G.

**BFS pseudocode:**

```text
frontier = queue containing initial state
explored = empty set
while frontier is not empty:
    node = remove from front of frontier
    if node is goal: return solution
    add node to explored
    for each action from node:
        child = apply action to node
        if child not in explored and not in frontier:
            add child to back of frontier
return failure
```

**BFS properties:**

| Property | Value | Explanation |
|---|---|---|
| Complete | YES | Will find solution if one exists (as long as branching factor is finite) |
| Optimal | YES | Finds shallowest (fewest steps) solution. Optimal if all step costs are equal. |
| Time Complexity | O(b^d) | Exponential in depth |
| Space Complexity | O(b^d) | Must store all nodes at current depth in frontier |

**Key weakness:** space complexity is brutal. With b=10 and d=10, you need to store 10 billion nodes. Memory runs out quickly.

### Depth-First Search (DFS)

**Strategy:** explore as deep as possible along one branch before backtracking. Uses a LIFO (Last In, First Out) stack, nodes added to the front and removed from the front.

**Visualise it:** go down one path as far as possible. If you hit a dead end, backtrack to the last decision point and try a different path. Using the same tree, DFS visits in the order A, B, E, F, C, D, G.

**DFS properties:**

| Property | Value | Explanation |
|---|---|---|
| Complete | NO (in infinite spaces) | Can get stuck going infinitely deep down one path |
| Optimal | NO | May find a deep solution when a shallower one exists |
| Time Complexity | O(b^m) | m = maximum depth, can be very large |
| Space Complexity | O(b*m) | Only needs to store the current path and siblings |

**Key strength:** space complexity is linear, far better than BFS. **Key weakness:** not complete or optimal. Can go infinitely deep.

### BFS vs DFS Comparison

| Feature | BFS | DFS |
|---|---|---|
| Data structure | Queue (FIFO) | Stack (LIFO) |
| Explores | Level by level | Branch by branch |
| Complete | Yes | No (infinite spaces) |
| Optimal | Yes (equal costs) | No |
| Time | O(b^d) | O(b^m) |
| Space | O(b^d) - BAD | O(b*m) - GOOD |
| Best when | Solution is shallow | Memory is limited |
| Worst when | Solution is deep | Graph is infinitely deep |

---

## Why Search Matters for AI

Search is one of the most fundamental techniques in AI. Before a machine can learn, it must know how to search. Examples:

- Google Maps uses search to find the shortest route
- Chess AI uses search to find the best move
- Puzzle solvers use search to find the solution sequence
- Robot path planning uses search to navigate obstacles

Road networks are essentially mazes: you start at a point, end at a point and have multiple ways to get there. How does Google Maps find the best route? Search algorithms.

---

## Key Terms for Week 6

| Term | Definition |
|---|---|
| Agent | An AI algorithm that determines optimal actions to reach a desired state |
| Goal-based agent | Plans ahead using foresight to achieve long-term objectives |
| Reflex agent | Acts immediately on current stimuli with no planning |
| State | A description of the current configuration of the world |
| Initial state | The starting configuration |
| Goal test | The condition that defines whether the goal has been reached |
| Path cost | The total cost of a sequence of actions |
| Search tree | A tree where nodes are states and edges are actions |
| Frontier | Nodes generated but not yet expanded |
| Branching factor (b) | Number of actions available from each state |
| Depth (d) | Level of a node in the tree |
| BFS | Breadth-First Search, explores level by level |
| DFS | Depth-First Search, explores depth first |
| Complete | An algorithm that always finds a solution if one exists |
| Optimal | An algorithm that always finds the best (lowest cost) solution |
| Time complexity | How the number of operations grows with problem size |
| Space complexity | How memory usage grows with problem size |
| Big O notation | Mathematical notation for describing algorithm complexity |
| Uninformed search | Search with no domain knowledge about which states are more promising |
