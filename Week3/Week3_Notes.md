# DG1AID - Week 3 Notes
## Unit 1 - Mathematics for AI and Data Science
### Aston University - Foundations of AI and Data Science (2025-26)

---

## Lecture Overview

Week 3 is the last week of Unit 1. It covers the mathematical foundations needed for AI and data science:
- Logic (propositional logic and truth tables)
- Sets and set operations
- Relations (including relation properties)
- Functions
- Graphs and networks (including adjacency matrices)

**Important note from the lecture:** Not everything in the quiz will be a calculation. There may be questions about theory. Not everything will require code. Bring pen and paper to the assessment.

---

## 1. Logic

### What is Propositional Logic?

When we use the word "logic" in maths and computing, we specifically mean **propositional logic**. This is the most fundamental form of logic and is the basis of all computer hardware.

A **proposition** is a statement that can be either TRUE or FALSE. It must be one of the two, not both, not neither.

**Examples of valid propositions:**
- "The motor is on" - either it is or it is not
- "Isaac is studying at Aston University" - either true or false
- "It is raining" - either true or false

**Examples that are NOT propositions:**
- "What did you eat today?" - this is a question, not a statement
- "9 - 10" - this is a mathematical expression with a numerical answer, not a true/false answer
- "Please close the door" - this is a command

**Quick test:** Put "it is true that..." in front of the statement. If it makes grammatical sense in English, it is a proposition.
- "It is true that the motor is on" - makes sense - IS a proposition
- "It is true that what did you eat today" - does not make sense - NOT a proposition

### Propositional Variables

Instead of writing full propositions every time, we abbreviate them with letters p, q, r...

Example:
- Let p = "the motor is on"
- Let q = "the light is on"
- Now we can write p ∧ q to mean "the motor is on AND the light is on"

True can be represented as T, 1, or the word "true"
False can be represented as F, 0, or the word "false"

---

### Logical Connectives

Connectives combine simple propositions into more complex ones. These are the building blocks of all computer logic.

| Symbol | Name | Other symbols you may see |
|---|---|---|
| ∧ | AND | &, · |
| ∨ | OR | \|, + |
| ¬ | NOT | ~, ! |
| ⇒ | IMPLIES | →, if...then... |
| ⇔ | IF AND ONLY IF | ↔, IFF |

---

### AND (Conjunction) - ∧

p ∧ q is true if and only if BOTH p and q are true.

| p | q | p ∧ q |
|---|---|---|
| T | T | **T** |
| T | F | F |
| F | T | F |
| F | F | F |

**Memory tip:** There is only ONE true result. Both must be true.

**Real example:** "The motor is on AND the temperature is safe" - both must be true for the system to run.

**Connection to hardware:** The AND logic gate passes voltage through only when both inputs have voltage.

---

### OR (Disjunction) - ∨

p ∨ q is true if AT LEAST ONE of p or q is true.

| p | q | p ∨ q |
|---|---|---|
| T | T | T |
| T | F | **T** |
| F | T | **T** |
| F | F | F |

**Memory tip:** There is only ONE false result - when both are false.

**Important:** This is the **inclusive OR** - it includes the case where both are true. There is also an **exclusive OR (XOR)** which does NOT allow both to be true. XOR is equivalent to NOT(p ⇔ q).

---

### NOT (Negation) - ¬

¬p is true if and only if p is false. It simply flips the value.

| p | ¬p |
|---|---|
| T | F |
| F | T |

**Real example:** If p = "the door is locked", then ¬p = "the door is not locked"

---

### IMPLIES (Conditional) - ⇒

p ⇒ q means "if p then q."

| p | q | p ⇒ q |
|---|---|---|
| T | T | T |
| T | F | **F** |
| F | T | T |
| F | F | T |

**This is the most confusing one.** The key insight: the ONLY way an implication is false is when the condition IS true but the result does NOT follow.

**Plain English explanation:** Your mum promises: "If you tidy your room, I will give you £10."
- p = "you tidy your room"
- q = "she gives you £10"

Row by row:
- Row 1: You DO tidy it, she DOES pay - promise kept - TRUE
- Row 2: You DO tidy it, she does NOT pay - promise broken - FALSE (the only false case)
- Row 3: You do NOT tidy it, she pays anyway - she was generous, but never broke the promise - TRUE
- Row 4: You do NOT tidy it, she does NOT pay - she never promised anything about untidy rooms - TRUE

**The key principle:** You can only break a conditional promise when the condition was met. If the condition was never triggered, the promise was never broken.

**Note on reversal:** p ⇐ q means "p is implied by q" - it is the same as q ⇒ p. The arrow direction matters.

---

### IF AND ONLY IF (Biconditional) - ⇔

p ⇔ q is true when p and q MATCH - both true or both false.

| p | q | p ⇔ q |
|---|---|---|
| T | T | **T** |
| T | F | F |
| F | T | F |
| F | F | **T** |

**Plain English:** Your mum now promises: "I will give you £10 IF AND ONLY IF you tidy your room."

This is a stricter promise in BOTH directions:
- If you tidy it, she will pay (same as IMPLIES)
- If you do NOT tidy it, she will NOT pay (NEW - this is the additional constraint)

Both sides must match. The difference from IMPLIES is row 3: here, if you do NOT tidy and she pays anyway, that breaks the deal (FALSE).

**Comparison:**

| | IMPLIES (⇒) | IFF (⇔) |
|---|---|---|
| p=T, q=T | TRUE | TRUE |
| p=T, q=F | FALSE | FALSE |
| p=F, q=T | **TRUE** | **FALSE** |
| p=F, q=F | TRUE | TRUE |

The ONLY difference is row 3. IMPLIES does not care what happens when p is false. IFF requires that both sides always match.

**IMPLIES** = one-way promise ("if this, then that")
**IFF** = two-way promise ("this happens exactly when that happens")

---

### Logic Gates and Computer Hardware

At the lowest hardware level, a CPU is just billions of logic gates made from silicon transistors.

- Input = applying voltage (TRUE) or not (FALSE)
- Output = passing voltage through the gate (TRUE) or not (FALSE)

The most important gates in practice:
- **NAND** (NOT AND) - apply NOT to the AND result. You can build an entire computer from only NAND gates.
- **NOR** (NOT OR) - apply NOT to the OR result. Also sufficient to build a complete computer.

---

## 2. Sets

### Definition

A **set** is the mathematical model for a collection of different things or objects. A set contains elements (also called members).

**Key properties of sets:**
- Order does NOT matter: {1, 2, 3} = {3, 2, 1} = {2, 1, 3}
- Repetition does NOT matter: {1, 2, 2, 3} = {1, 2, 3}
- Sets are written with **curly brackets {}**

**Notation:**
- "m is an element of S": m ∈ S (the E-like symbol means "belongs to")
- "b is not an element of S": b ∉ S (same symbol with a line through)
- In Python, sets can be represented as NumPy arrays (though Python arrays do preserve order)

### Three Ways to Write a Set

**1. Verbal notation:**
Let S be the set of letters in the word "mathematics"

**2. Roster notation (listing all elements):**
{m, a, t, h, e, m, a, t, i, c, s} = {a, c, e, h, i, m, s, t}
(duplicates removed, order does not matter)

**3. Set-builder notation:**
{x | x is a letter in 'mathematics'}
This reads as "the set of all x such that x is a letter in mathematics"

---

### Set Operations

These operations combine or compare sets. They use the same underlying logic as the connectives above.

**Intersection (∩) - AND**
Elements that are in BOTH sets.
- A ∩ B = {x | x ∈ A AND x ∈ B}
- Example: {1,2,3} ∩ {2,3,4} = {2,3}
- **Colab connection:** This is exactly what you coded using np.intersect1d() in Lab II

**Union (∪) - OR**
Elements that are in AT LEAST ONE of the sets.
- A ∪ B = {x | x ∈ A OR x ∈ B OR x ∈ A∩B}
- Example: {1,2,3} ∪ {2,3,4} = {1,2,3,4}

**Difference (A - B or A\B)**
Elements that are in A but NOT in B.
- A - B = {x | x ∈ A AND x ∉ B}
- Example: {1,2,3} - {2,3,4} = {1}
- Note: A - B ≠ B - A (order matters for difference)

**Symmetric Difference (AΔB)**
Elements that are in EITHER set but NOT in the intersection.
- AΔB = (A ∪ B) - (A ∩ B)
- Example: {1,2,3} Δ {2,3,4} = {1,4}

**Complement (A' or Ā or Ac)**
Elements NOT in A (within a defined universe Ω).
- A' = {x | x ∉ A}
- Example: If universe Ω = {1,2,3,4,5} and A = {1,2}, then A' = {3,4,5}

---

### Subsets

**Subset (⊆):**
T is a subset of S if every element in T is also in S.
- T ⊆ S means "T is a subset of S"
- T ⊄ S means "T is not a subset of S"
- {1,2,3} ⊆ {1,2,3,4} - TRUE (all elements of the left set are in the right set)
- {1,2,3,4} ⊆ {1,2} - FALSE (4 is not in {1,2})
- A set is always a subset of itself: {1,2,3} ⊆ {1,2,3}

**Proper Subset (⊂):**
T is a proper subset of S if every element in T is also in S AND T does not equal S.
- T ⊂ S means "T is a proper subset of S" (T is strictly smaller)
- {1,2,3} ⊂ {1,2,3,4} - TRUE (it is a proper subset, the sets are not equal)
- {1,2,3} ⊂ {1,2,3} - FALSE (they are equal, so not a proper subset)

**Empty Set (∅):**
The set containing no elements at all.
- ∅ or {} (empty curly brackets)
- CAREFUL: {∅} is NOT the empty set - it is a set containing one element (the empty set itself)
- The empty set is a subset of EVERY set: ∅ ⊆ {1,2,3}

---

### Power Sets

The power set P(S) is the set containing ALL possible subsets of S (including the empty set and S itself).

Example: P({1,2,3}) = {∅, {1}, {2}, {3}, {1,2}, {1,3}, {2,3}, {1,2,3}}

**Key fact:** If S has n elements, its power set always has 2ⁿ elements.
- {1,2,3} has 3 elements → power set has 2³ = 8 elements (count above: 8 ✓)
- {a,b} has 2 elements → power set has 2² = 4 elements: {∅, {a}, {b}, {a,b}}

---

### Commonly Used Number Sets

| Symbol | Name | Contents |
|---|---|---|
| ℕ | Natural numbers | {1, 2, 3, 4, ...} (some include 0) |
| ℤ | Integers | {..., -2, -1, 0, 1, 2, ...} |
| ℚ | Rational numbers | All fractions: {1/2, 2/3, -7/11, ...} |
| ℝ | Real numbers | Everything on the number line: {π, e, √2, ...} |

**Relationship:** ℕ ⊂ ℤ ⊂ ℚ ⊂ ℝ (each is a proper subset of the next)

---

## 3. Relations

### Cartesian Product

Before defining relations, we need the Cartesian product.

If S = {1, 2, 3} and T = {A, B, C}, then:
S × T = {(1,A), (1,B), (1,C), (2,A), (2,B), (2,C), (3,A), (3,B), (3,C)}

This gives all possible ordered pairs where the first element is from S and the second is from T.

**Important:** T × S ≠ S × T (order matters for Cartesian products)

### Tuples vs Sets

This distinction is critical:
- **Sets** use curly brackets, do NOT care about order or repetition: {1,2} = {2,1} = {1,2,2}
- **Tuples** use round brackets, DO care about order and repetition: (1,2) ≠ (2,1) ≠ (1,2,2)

### Definition of a Relation

A relation is a set of tuples (ordered pairs) that describes how elements from one set connect to elements of another set.

Example:
- S = {1, 2, 3} and T = {A, B, C}
- Relation R = "is the position in the alphabet of": {(1,A), (2,B), (3,C)}
- "1 is the position in the alphabet of A" ✓

A relation is essentially a subset of the Cartesian product S × T.

---

### Properties of Relations

A relation on a single set A (where both the input and output come from A) can have these properties:

**Reflexive:** Every element relates to itself.
- For every x in A, (x, x) is in the relation
- Example on A = {1,2,3}: {(1,1), (2,2), (3,3)} ✓
- Think: every node has an arrow back to itself in a graph

**Symmetric:** If x relates to y, then y also relates to x.
- For every (x,y) in the relation, (y,x) is also in the relation
- Example: {(1,2), (2,1), (3,3)} ✓
- Think: every arrow has a corresponding reverse arrow

**Transitive:** If x relates to y, and y relates to z, then x also relates to z.
- If (x,y) and (y,z) are in the relation, then (x,z) must also be in the relation
- Example: {(1,2), (2,3), (1,3)} ✓ - because 1→2 and 2→3, we need 1→3
- Think: if A leads to B and B leads to C, then A can reach C directly

---

## 4. Functions

### Definition

A function is a special type of relation where every input maps to exactly one output. There must be no ambiguity - every input must have exactly one corresponding output.

A function that maps from set A (domain) to set B is written: f: A → B

### Key Terms

| Term | Definition | Example for f(x) = x² |
|---|---|---|
| Domain | The set of ALL POSSIBLE inputs | ℝ (can square any number) |
| Codomain | The set of ALL ACTUAL outputs produced | ℝ⁺ ∪ {0} (squares are always ≥ 0) |
| Range | The set of all POSSIBLE output values | ℝ (technically, but f(x)=x² never gives negatives) |

**Note:** The range and codomain are often the same but not always. For f(x) = x², the domain is ℝ but the codomain is only ℝ⁺ ∪ {0} because squaring never gives a negative output.

**Well-defined functions:** For a function to be valid, each input must map to EXACTLY ONE output. f(x) = √x is not well-defined for negative inputs (and gives two outputs ±√x for positive inputs unless we restrict to positive outputs).

### Types of Functions

| Type | Property | Description | Example |
|---|---|---|---|
| Injective (one-to-one) | Left-unique | Each input maps to a UNIQUE output. No two inputs give the same output. | f(x) = 2x |
| Surjective (onto) | Right-total | Every possible output is produced by at least one input. | f(x) = x³ |
| Bijective | Both injective and surjective | Perfect one-to-one correspondence. Every output is produced exactly once. | f(x) = x |
| General function | Neither | Multiple inputs can map to the same output, and some outputs are unreachable. | f(x) = x² over ℝ |

**Python connection:** The relu function you wrote in Lab II is a function:
- Domain: all real numbers (ℝ)
- Codomain: ℝ⁺ ∪ {0} (only non-negative outputs)
- Not injective (relu(-1) = relu(-5) = 0)
- Not surjective over ℝ (negative outputs never produced)

---

## 5. Graphs and Networks

### Two Meanings of "Graph"

In everyday language, "graph" usually means a chart (bar chart, line chart, pie chart). In mathematics, "graph" means something completely different - **a network of connected points**. We will use the mathematical meaning.

### Definition of a Graph

A graph G consists of three components:

1. **V** - a set of **vertices** (also called nodes, sites, or points) - the objects
2. **E** - a set of **edges** (also called links, connections, or lines) - the relationships
3. **I** - the **incidence function** - a set of tuples showing which vertices are connected by which edges

**Example:**
- V = {1, 2, 3, 4}
- E = {a, b, c, d, e}
- I = {(1,2), (1,4), (2,3), (2,4), (3,4)}

The same graph can be drawn in many different ways - what matters is the connections, not the spatial layout.

### A Network (Applied Graph)

A network is just a graph applied to real-world objects:
- Vertices become **nodes** (computers, people, cities, websites)
- Edges become **links** (cables, friendships, roads, hyperlinks)
- Used to represent and visualise real-world data

---

### Types of Graphs

**Undirected Graph:**
Edges can be traversed in EITHER direction. If A connects to B, then B connects to A.
- Example: Facebook friendship - if you are friends with someone, they are friends with you
- Adjacency matrix is symmetric

**Directed Graph (Digraph):**
Edges can only be traversed in ONE direction. The direction of the arrow matters.
- Example: Twitter/X following - you can follow someone without them following you back
- Adjacency matrix is NOT necessarily symmetric

**Weighted Graph:**
Edges have numerical labels representing some quantity (distance, time, cost, strength).
- Example: Road network where edge weights represent travel time between junctions
- Example: Neural network where edge weights represent connection strengths

**Unweighted Graph:**
Edges simply show that two vertices are connected. No additional information on the edge.

---

### Adjacency Matrix

An **adjacency matrix** is a way to represent a graph mathematically as a grid of numbers.

**How to construct one:**
- Create an n × n matrix where n is the number of vertices
- Label both rows and columns with vertex names
- Put 1 at position (i,j) if vertex i is connected to vertex j
- Put 0 at position (i,j) if vertex i is NOT connected to vertex j
- For weighted graphs: replace the 1s with the actual weight values
- For directed graphs: only put 1 in one direction (not symmetric)

**Example - Undirected, unweighted graph with 4 vertices:**
Edges: 1-2, 1-4, 2-3, 2-4, 3-4

```
    1  2  3  4
1 [ 0  1  0  1 ]
2 [ 1  0  1  1 ]
3 [ 0  1  0  1 ]
4 [ 1  1  1  0 ]
```

Note: the matrix is symmetric (A[i][j] = A[j][i]) because undirected edges go both ways.

**For a directed graph:** Only put 1 in the direction of the arrow. If 1→2 but not 2→1, put 1 at (1,2) but 0 at (2,1).

**For a weighted graph:** Replace the 1s with the weight values (e.g. distance in miles, time in minutes).

---

### Examples of Graphs in the Real World

| Application | Vertices | Edges | Type |
|---|---|---|---|
| Social network (Facebook) | People | Friendships | Undirected, unweighted |
| Social network (Twitter) | People | Follows | Directed, unweighted |
| Road network | Junctions | Roads | Undirected, weighted (distance/time) |
| Internet | Web pages | Hyperlinks | Directed, unweighted |
| Neural network | Neurons | Connections | Directed, weighted (connection strength) |
| Premier League fixtures | Teams | Matches | Directed (home/away), weighted (dates) |
| Transport network | Stations | Routes | Undirected, weighted (journey time) |

### Relation Properties Visualised as Graphs

The three relation properties from earlier can be visualised using graphs:
- **Reflexive** - every vertex has a self-loop (an arrow pointing to itself)
- **Symmetric** - every edge has a corresponding reverse edge (undirected graph)
- **Transitive** - if there is a path A→B→C, there must also be a direct edge A→C

---

### Why Graphs Matter for AI

Graphs are fundamental to AI and data science. You will use them extensively in later weeks:

- **Search algorithms (Weeks 6-8)** - BFS, DFS, A* and Dijkstra's algorithm all work by traversing graphs
- **Neural networks** - are themselves weighted directed graphs
- **Social network analysis** - understanding communities, influence, information spread
- **Knowledge graphs** - representing relationships between concepts
- **Route planning** - Google Maps is a weighted graph problem

---

## Week 3 Lab Connection

The Week 3 lab covers data handling in Python using NumPy, Pandas and Matplotlib. The key connection to this lecture:

- **Sets in Python:** Arrays and NumPy arrays can represent sets. np.intersect1d() computes the intersection of two arrays (exactly like the set operation A ∩ B).
- **Matrices:** NumPy matrices are used to represent data. An adjacency matrix for a graph can be stored as a NumPy array.
- **Functions in Python:** Every Python function you write is a mathematical function in the sense defined above.

---

## Key Concepts Summary for Quiz

| Concept | Key point to remember |
|---|---|
| Proposition | Statement that is TRUE or FALSE. Test: "it is true that..." must make grammatical sense |
| AND (∧) | Only true when BOTH are true |
| OR (∨) | True when AT LEAST ONE is true |
| NOT (¬) | Flips the truth value |
| IMPLIES (⇒) | Only FALSE when p=True and q=False |
| IFF (⇔) | True when both MATCH (both T or both F) |
| Set | Collection of distinct elements. No order, no duplicates. |
| Intersection (∩) | Elements in BOTH sets |
| Union (∪) | Elements in EITHER set |
| Subset (⊆) | Every element of T is also in S |
| Power set | All possible subsets. Size = 2ⁿ |
| Relation | Set of tuples describing connections between elements |
| Reflexive | Every element relates to itself |
| Symmetric | x→y implies y→x |
| Transitive | x→y and y→z implies x→z |
| Function | Relation where each input maps to EXACTLY ONE output |
| Injective | Each input maps to a unique output |
| Bijective | Both injective and surjective |
| Graph | Vertices + edges + incidence function |
| Undirected | Edges go both ways |
| Directed | Edges go one way only |
| Weighted | Edges have numerical labels |
| Adjacency matrix | Grid showing connections: 1=connected, 0=not connected |
