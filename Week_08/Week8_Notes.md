# DG1AID - Week 8 Notes
## Unit 3 - Constraint Satisfaction Problems and Nature-Inspired Algorithms

---

## Lecture Overview

Week 8 covers two topics:

1. Constraint Satisfaction Problems (CSPs), a different way of formulating and solving problems
2. Nature-Inspired Algorithms, how nature inspires search and optimisation

---

## What is a CSP?

In traditional search algorithms, each state is treated as an atomic black box with no internal structure. You just check whether a state is the goal or not.

CSPs are different. In a CSP:

- Each state has internal structure, it consists of variables that need to be assigned values
- Not all assignments are valid, there are constraints that must be satisfied
- A solution is found when all variables are assigned values that satisfy all constraints

Russell and Norvig: "Such constraint satisfaction problems are solved when each variable in the problem has a value that satisfies all the constraints."

In one sentence: we assign values to variables so that no rules are broken.

### Formal Definition of a CSP

A CSP consists of three components:

1. **Variables:** X1, X2, ..., Xn, the things that need to be assigned values
2. **Domains:** D1, D2, ..., Dn, the set of possible values for each variable
3. **Constraints:** relations restricting which combinations of values are allowed

### Assignment Terminology

| Term | Definition |
|---|---|
| Empty assignment | No variables have been assigned yet |
| Partial assignment | Some variables have been assigned |
| Complete assignment | Every variable has been assigned a value |
| Consistent assignment | No constraints are violated |
| Partial solution | A partial assignment that is consistent |
| Solution | A complete and consistent assignment |

---

## Real-World Example: Map Colouring

The problem: colour a map of Australia so that no two adjacent regions have the same colour, using as few colours as possible.

**CSP formulation:**

- Variables: WA, NT, Q, SA, NSW, V, T (7 Australian regions)
- Domain: D = {yellow, green, blue} (3 colours)
- Constraints: adjacent regions must have different colours

**Binary constraints** (pairs of regions that cannot share a colour): C = {WA!=NT, WA!=SA, NT!=SA, NT!=Q, SA!=Q, SA!=NSW, SA!=V, Q!=NSW, NSW!=V}

Note: Tasmania (T) has no constraints because it is an island and does not touch any other region.

Example solution: {WA=yellow, NT=green, Q=yellow, NSW=green, V=yellow, SA=blue, T=blue}

**Graph representation:** the map can be represented as an undirected graph where nodes are regions and edges are adjacencies (the constraint that those two must differ). This is called a constraint graph.

**Adjacency matrix for Australia** (1 = adjacent/constrained, 0 = not adjacent):

```text
       WA  NT  SA  Q  NSW  V  T
WA   [  0   1   1  0   0   0  0 ]
NT   [  1   0   1  1   0   0  0 ]
SA   [  1   1   0  1   1   1  0 ]
Q    [  0   1   1  0   1   0  0 ]
NSW  [  0   0   1  1   0   1  0 ]
V    [  0   0   1  0   1   0  0 ]
T    [  0   0   0  0   0   0  0 ]
```

South Australia (SA) is constrained against every mainland neighbour, which is why it drives most of the difficulty in this particular map. Tasmania's row and column are all zero since it is an island with no shared border.

### Other Real-World CSP Examples

| Problem | Variables | Domain | Constraints |
|---|---|---|---|
| Sudoku | 81 cells | {1-9} | Each digit appears once per row, column and 3x3 box |
| 8-Queens | 8 queens | Board positions | No two queens attack each other |
| University timetabling | Course-room-time assignments | Rooms, times, days | No two courses in same room at same time, teacher not double-booked |
| Nurse scheduling | Nurse-shift assignments | Yes/No | Minimum staffing levels, maximum shifts per week |
| Champions League draw | Team-fixture assignments | Opponents, home/away | Teams cannot face same-nation opponents, cannot play same team twice |

---

## Why Not Just Use BFS or DFS?

For the Australia map colouring problem with 5 neighbouring variables and 3 colours:

- Naive search: 3^5 = 243 possible assignments to check
- With constraints: only 3^2 = 32 assignments (constraints eliminate most combinations)
- Adding constraints dramatically reduces the search space

But even with constraints, naive BFS on CSPs generates enormous trees. A smarter approach is needed.

---

## CSP Search: Backtracking Search

**Strategy:** DFS with constraint checking at every step. As soon as an assignment violates a constraint, backtrack and try a different value instead of continuing to a dead end.

Two key improvements over naive DFS:

1. Assign one variable at a time (rather than all at once)
2. Check constraints as you go (stop early when a violation is detected)

**Pseudocode:**

```text
BACKTRACK(assignment):
    if assignment complete: return assignment
    select unassigned variable
    for each value in domain:
        if consistent (no constraints violated):
            add value to assignment
            result = BACKTRACK(assignment)
            if result is not failure: return solution
            remove value from assignment
    return failure
```

**Why backtracking is better:** by checking constraints at every step, we avoid exploring branches that cannot possibly lead to a solution. In the Australia example, backtracking finds a solution in 10 operations versus 15+ for naive search without even solving it.

Further improvements to backtracking (not covered in depth in this module):

- Forward checking: when a variable is assigned, eliminate inconsistent values from neighbours' domains
- Arc consistency: propagate constraints through the network
- Heuristics for variable and value ordering

---

## CSP Search: Local Search (Min-Conflicts)

A completely different approach: instead of building a solution incrementally, start with a random complete assignment and repair it.

**Strategy:**

1. Start with a random complete assignment (may violate constraints)
2. Find a variable that is causing a conflict
3. Change its value to the one that minimises conflicts
4. Repeat until no conflicts remain

**Min-conflicts pseudocode:**

```text
LOCAL_SEARCH(max_steps):
    current = random complete assignment
    for i = 1 to max_steps:
        if consistent: return current
        var = randomly chosen conflicted variable
        val = value that minimises conflicts for var
        set var = val in current
    return failure
```

**Why we need max_steps:** local search can get stuck in local optima (stuck states where no single change improves things). Setting a max prevents infinite loops.

Solutions when stuck:

- Random restarts (start again with a new random assignment)
- Random tie-breaking (when multiple values minimise conflicts equally)

### Backtracking vs Local Search Comparison

| Feature | Backtracking | Local Search |
|---|---|---|
| Initial state | Empty assignment | Random complete assignment |
| Approach | Explore and prune | Adjust and repair |
| Constraints | Checked after each assignment | Violations allowed, then reduced |
| Guarantees solution | Yes (if finite) | No, may get stuck |
| Memory use | Low (DFS-based) | Very low |
| Scalability | Moderate | Often good |
| Question asked | "Can I extend this partial solution?" | "How bad is the current solution and how can I improve it?" |

---

## CSPs and Modern AI

CSPs are not just classic techniques, they underpin many modern AI systems:

**SAT (Boolean Satisfiability) Solvers:**

- Program verification and software testing
- Circuit design and testing
- Security analysis

**Scheduling and Resource Allocation:**

- University timetabling
- Manufacturing planning
- Cloud computing resource allocation

**Hybrid and Neuro-Symbolic AI:**

- Deep learning learns patterns, constraint solving enforces rules
- Program synthesis
- Formal verification of AI systems

**AI Planning and Robotics:**

- Multi-agent coordination (relies heavily on constraint reasoning)
- Robot motion planning

---

## Nature-Inspired Algorithms

A brief introduction to how nature inspires search and optimisation algorithms.

Many natural systems solve complex optimisation problems, deal with many constraints, without central control, with limited local information, at massive scale and in challenging environments.

Nature does not compute optimal solutions analytically. Instead it uses parallelism, random variation, feedback loops, selection pressure, self-organisation and social information.

### Ant Colony Optimisation (ACO)

Developed by Marco Dorigo in the early 1990s.

**Inspiration:** ants find shortest paths between nest and food using pheromone trails.

- Ants lay pheromone as they walk
- Other ants follow stronger pheromone trails
- Shorter routes have stronger pheromone (more passes per unit time)
- The system is completely decentralised and massively parallel

**Application:** the Travelling Salesman Problem (TSP), find the shortest route visiting n cities exactly once.

**Why this is hard, the TSP scale problem:** for n cities there are (n-1)!/2 unique tours. With a supercomputer checking 1 billion tours per second:

- 20 cities: 2 years
- 30 cities: 140 trillion years (10,000 times the age of the Universe)
- 40 cities: no point calculating
- 50 cities: number of tours exceeds the number of atoms in the Universe

This is why ACO and other heuristic approaches are necessary, brute force is completely impossible.

### Particle Swarm Optimisation (PSO)

Developed by Kennedy and Eberhart in the mid-1990s.

**Inspiration:** bird flocking, fish schooling, insect swarming, decentralised social behaviour.

**How it works:**

- Each particle represents a candidate solution (a point in the search space)
- Particles move around the space semi-randomly
- Each particle remembers its own best position so far
- Each particle is attracted to the neighbourhood's best position so far
- Balances exploration (try new areas) and exploitation (refine known good areas)

**Applications:** mathematical optimisation, engineering design, neural network training.

### Evolutionary Algorithms (EAs)

Inspired by Darwin's evolution by natural selection.

**Motivation:** if evolution can find biological solutions to the problem of survival, we can use it to find computational solutions to mathematical problems.

**Generic EA process:**

1. Randomly generate an initial population of solutions
2. Evaluate the "fitness" of each solution
3. Check if the goal has been reached
4. Select individuals to be parents (based on fitness, better solutions more likely to be selected)
5. Produce new solutions through reproduction, using recombination (combining two parents) and mutation (random changes)
6. Remove individuals with lower fitness
7. Return to step 2

**Examples of EA variants:**

| Algorithm | Key Idea | Developed |
|---|---|---|
| Genetic Algorithms (GAs) | Population-based search with crossover and mutation | Holland (1975) |
| Genetic Programming | Evolves programs and symbolic expressions | Koza (1992) |
| Evolutionary Strategies | Continuous optimisation | Rechenberg (1965) |
| Particle Swarm Optimisation | Social swarm behaviour | Kennedy and Eberhart (1995) |
| Ant Colony Optimisation | Pheromone trails | Dorigo (1990s) |

**Applications:** evolving virtual creatures, spacecraft antenna design, evolving code, scheduling, evolving 3D printed robot bodies.

---

## Unit 3 Summary

By the end of Unit 3, you should understand that:

- Intelligence can be viewed as structured search through possibility spaces
- Heuristics are early forms of domain knowledge integration
- CSPs model reasoning under constraints (scheduling, planning, configuration)
- Search is still used in modern AI: planning, robotics, games
- Even modern ML systems search over model architectures and optimise objective functions

Before machines can learn, they must know how to search. Before they can optimise, we must understand complexity. Before we build intelligence, we must understand problem structure.

---

## Key Terms for Week 8

| Term | Definition |
|---|---|
| CSP | Constraint Satisfaction Problem, assign values to variables satisfying all constraints |
| Variable | Something in a CSP that needs to be assigned a value |
| Domain | The set of possible values a variable can take |
| Constraint | A rule restricting which combinations of values are allowed |
| Binary constraint | A constraint between exactly two variables |
| Consistent assignment | An assignment that does not violate any constraints |
| Complete assignment | Every variable has been assigned a value |
| Solution | A complete and consistent assignment |
| Constraint graph | A graph where nodes are variables and edges are constraints between them |
| Backtracking search | DFS with constraint checking, backtracks when a violation is detected |
| Local search | Starts with a complete assignment and repairs violations |
| Min-conflicts heuristic | Choose the value that minimises the number of constraint violations |
| ACO | Ant Colony Optimisation, inspired by pheromone trails |
| PSO | Particle Swarm Optimisation, inspired by bird flocking |
| Evolutionary Algorithm | Search inspired by Darwin's natural selection |
| TSP | Travelling Salesman Problem, find shortest tour visiting all cities |
| Fitness | A measure of how good a solution is in evolutionary algorithms |
