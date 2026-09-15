# DG1AID - Week 7 Notes
## Unit 3 - Solving Problems by Search (Part II)

---

## Lecture Overview

Week 7 continues search algorithms, introducing more advanced uninformed search and then informed (heuristic) search:

- Depth-Limited Search (DLS)
- Iterative Deepening Search (IDS)
- Informed search and heuristics
- Greedy Best-First Search
- A* Search

---

## Recap: Problem Examples

**Tower of Hanoi:** move all disks from one peg to another. Rules: only move one disk at a time, never place a larger disk on a smaller one. Classic search problem, the search tree grows exponentially with the number of disks.

**Sudoku:** fill a 9x9 grid so every row, column and 3x3 box contains digits 1-9. This is a Constraint Satisfaction Problem (covered in Week 8) as well as a search problem.

**8-Queens:** place 8 queens on a chessboard so none attack each other. Another CSP, the search tree is enormous if done naively.

**4-Colour Theorem:** any map can be coloured with 4 colours such that no two adjacent regions share a colour. This is the classic graph colouring CSP.

---

## More Uninformed Search Algorithms

### Depth-Limited Search (DLS)

The problem with DFS: it can go infinitely deep. Solution: put a depth limit.

**Strategy:** same as DFS but stop exploring a branch when it reaches depth limit l. Nodes beyond depth l are treated as having no children.

**DLS properties:**

| Property | Value | Explanation |
|---|---|---|
| Complete | NO | If solution is deeper than limit l, it will not be found |
| Optimal | NO | May not find shortest path |
| Time | O(b^l) | Exponential in depth limit |
| Space | O(b*l) | Linear space like DFS |

**Key problem:** how do you choose the depth limit? Too small and you miss the solution. Too large and you waste time.

### Iterative Deepening Search (IDS)

The best of both worlds: combines the space efficiency of DFS with the completeness and optimality of BFS.

**Strategy:** run DLS repeatedly with increasing depth limits: 0, 1, 2, 3, 4... until a solution is found.

```text
DLS(limit=0) -> DLS(limit=1) -> DLS(limit=2) -> DLS(limit=3) -> ... -> solution found
```

This seems wasteful, you re-explore earlier levels many times. In practice the extra work is minimal because most nodes are at the deepest level.

**Why it works:** with branching factor b=10, at depth d=4:

- Nodes at depth 4: 10,000
- Nodes at depths 0-3 re-explored: ~1,111
- Re-exploration overhead: about 11%, a small price for the benefits

**IDS properties:**

| Property | Value | Explanation |
|---|---|---|
| Complete | YES | Will find solution at any depth |
| Optimal | YES | Finds shallowest solution first |
| Time | O(b^d) | Same as BFS |
| Space | O(b*d) | Same as DFS, excellent |

IDS is usually the best uninformed search algorithm because it is complete, optimal and memory efficient.

### Summary Table: All Uninformed Search Algorithms

| Algorithm | Complete | Optimal | Time | Space |
|---|---|---|---|---|
| BFS | Yes | Yes (equal costs) | O(b^d) | O(b^d) |
| DFS | No | No | O(b^m) | O(b*m) |
| DLS | No | No | O(b^l) | O(b*l) |
| IDS | Yes | Yes (equal costs) | O(b^d) | O(b*d) |

Where b = branching factor, d = depth of shallowest solution, m = max depth, l = depth limit.

IDS dominates: it has the same completeness and optimality as BFS but uses only the memory of DFS.

---

## Informed (Heuristic) Search

The problem with uninformed search: it has no idea which states are more promising. It treats all unexplored states equally.

The solution: use domain knowledge to guide the search towards the goal faster.

Informed search uses a heuristic function h(n) that estimates how far the current node n is from the goal. It is a guess based on domain knowledge.

### What is a Heuristic?

A heuristic is a rule of thumb or educated guess that helps guide decision-making without guaranteeing an optimal solution.

For search problems: h(n) = estimated cost from node n to the goal state.

**Example - finding shortest route between cities:**

- h(n) = straight-line distance from current city to destination
- This is always an underestimate (you cannot travel in a perfectly straight line)
- Called the "as the crow flies" distance

**Properties of a good heuristic:**

- Should never overestimate the true cost (this is called being admissible)
- Should be as close to the true cost as possible (more accurate means faster search)
- Should be computationally cheap to calculate

### Cost Functions

For informed search we need to define costs carefully:

- **g(n)** = the actual cost from the initial state to node n (path cost so far)
- **h(n)** = the estimated cost from node n to the goal (heuristic)
- **f(n) = g(n) + h(n)** = estimated total cost of the cheapest solution through node n

---

## Greedy Best-First Search

**Strategy:** always expand the node that appears to be closest to the goal according to the heuristic h(n). Ignores g(n) completely, only uses h(n).

Like a greedy person: always makes the locally best choice without thinking about the overall path cost.

| Property | Value | Explanation |
|---|---|---|
| Complete | No | Can get stuck in loops |
| Optimal | No | May find a path that looks good locally but is not the best overall |
| Time | O(b^m) | Bad in worst case |
| Space | O(b^m) | Must store all nodes |

**Key weakness:** greedy search can be fooled by a heuristic that looks good locally but leads to a longer overall path. It is like taking the road that looks closest to your destination but ends up going around a mountain.

---

## A* Search

A* (pronounced "A-star") is the most important and widely used informed search algorithm.

**Strategy:** expand the node with the lowest f(n) = g(n) + h(n). This balances the actual cost already paid (g) against the estimated remaining cost (h).

**Why A* is brilliant:** by considering both g(n) and h(n) together, A* finds the optimal path if the heuristic is admissible.

**A* properties:**

| Property | Value | Explanation |
|---|---|---|
| Complete | Yes | Will find solution if one exists |
| Optimal | Yes, if h(n) is admissible | Finds the lowest cost solution |
| Time | O(b^d) in best case | Depends heavily on heuristic quality |
| Space | O(b^d) | Must store all generated nodes |

### Admissible Heuristic

A heuristic h(n) is admissible if it never overestimates the true cost to the goal.

**Why this matters:** if h(n) overestimates, A* might skip over the optimal solution thinking it is too expensive. With an admissible heuristic, A* is guaranteed to find the optimal path.

Example: straight-line distance to destination is admissible because the actual road distance is always greater than or equal to the straight-line distance.

### Inadmissible Heuristic

If h(n) overestimates sometimes, A* is no longer guaranteed to find the optimal solution. It may find a solution, but not necessarily the best one.

---

## Greedy vs A* Comparison

| Feature | Greedy Best-First | A* |
|---|---|---|
| Evaluation function | h(n) only | f(n) = g(n) + h(n) |
| Complete | No | Yes |
| Optimal | No | Yes (admissible h) |
| Speed | Faster (ignores g) | Slightly slower but correct |
| Use when | Speed matters, optimality not critical | Optimality required |

---

## Practical Examples of Heuristics

**Route Finding (Google Maps):**

- h(n) = straight-line distance from current location to destination
- Always admissible (straight line is always shorter than or equal to road distance)
- A* with this heuristic finds the optimal route

**8-Puzzle:**

- h(n) = number of tiles in the wrong position (Hamming distance)
- h(n) = sum of Manhattan distances of each tile from its goal position
- Manhattan distance heuristic is more informative and leads to faster search

```text
Manhattan distance for one tile:
tile currently at (row 2, col 0), goal position (row 0, col 1)
distance = |2 - 0| + |0 - 1| = 2 + 1 = 3
```

**Pathfinding in Games:**

- A* is the standard algorithm for character movement in video games
- h(n) = Euclidean or Manhattan distance to destination
- Interactive visualiser: [qiao.github.io/PathFinding.js/visual](http://qiao.github.io/PathFinding.js/visual/)

---

## Which Heuristic to Choose?

When multiple admissible heuristics are available, choose the one with the highest h(n) values (closest to the true cost), this is called the dominant heuristic.

A more informed heuristic expands fewer nodes and finds the solution faster.

If h1(n) >= h2(n) for all n, then h1 dominates h2 and is the better choice.

---

## Key Terms for Week 7

| Term | Definition |
|---|---|
| DLS | Depth-Limited Search, DFS with a depth limit |
| IDS | Iterative Deepening Search, DLS with increasing limits |
| Informed search | Search that uses domain knowledge to guide exploration |
| Heuristic function h(n) | Estimated cost from node n to the goal |
| g(n) | Actual cost from initial state to node n |
| f(n) | g(n) + h(n), estimated total solution cost through n |
| Greedy Best-First Search | Expands node with lowest h(n) only |
| A* Search | Expands node with lowest f(n) = g(n) + h(n) |
| Admissible heuristic | Never overestimates the true cost to the goal |
| Dominant heuristic | The heuristic with higher h values, leads to faster search |
| Straight-line distance | Classic admissible heuristic for route finding |
| Manhattan distance | Sum of horizontal and vertical distances, used in grid problems |
