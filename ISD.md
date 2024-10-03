## Puran Paodensakul , 6611140, 542


## Comments and Answers on Path-Finding Search Procedures

### 1. Comment on the following quote:
"One of the main goals of AI should be to build general heuristics applicable to any graph-searching problem."

**Comment:**
The goal emphasizes developing versatile strategies that can solve various graph search issues. However, it does not specify which particular path-finding search procedure is fair or how it applies to different types of graphs. This highlights the need for flexible and adaptable heuristics that can cater to a wide range of graph-searching problems without being limited to specific procedures.

### 2. Which of the path-finding search procedures is fair in that any element on the frontier will eventually be chosen?

**Answer:**

- **Finite graphs without cycles:** Breadth-First Search (BFS) is fair because it ensures that every node at a given depth level will be visited before moving to the next deeper level.
- **Finite graphs with cycles:** BFS may not guarantee that every node will be visited because it can get stuck in a cycle and keep revisiting the same nodes infinitely.
- **Infinite graphs (with finite branching factors):** BFS is fair because it will visit nodes level by level, ensuring that any element on the frontier will eventually be chosen.

### 3. What happens if the heuristic function is not admissible but is still nonnegative (assume an A* search)?

**Answer:**
If the heuristic function used in A* search is not admissible, it may overestimate or underestimate the cost to reach the goal from a given node. In such cases, A* search might not find the optimal solution because it could expand nodes that are less likely to lead to the goal. However, it will still produce a feasible solution and guarantee finding a path if one exists.

### 4. Statement and Proof of the Optimality of A*

**Statement:**
The A* search algorithm is optimal when using an admissible heuristic function (h(n) ≤ h*(n), where h*(n) is the real cost from node n to the goal). This means that if there exists any solution, A* will find the shortest one among all solutions.

**Formal Proof:**
Let G be a graph with start node s and goal node g. Suppose we have an admissible heuristic function h(n) for every node n in G. Consider two paths p1 from s to some node v, and p2 from v to the goal g. If p1 is not optimal (i.e., there exists a shorter path p3 from s to g), then we have:  
cost(p1) + h(v) > cost(p3). Since h(n) ≤ h*(n), it follows that h(v) < cost(pvg). Therefore, the total cost of p2 is greater than or equal to the sum of costs for both paths p1 and p2:  
cost(p2) >= cost(p1) + cost(pvg) > cost(p3) + cost(p1), which contradicts the assumption that p2 is a shorter path from s to g. Thus, A* will find an optimal solution if one exists using an admissible heuristic function in this class of algorithms.

###  5. Genetic Algorithm Results

### Initial Chromosome Generations, Crossover, and Mutation

**Chromosome (a,b,c,d) | Fitness Value | Likelihood**

1. (3,21,4,5) | \( |77-50| = 27 \) | 25.20%
2. (7,30,8,3) | \( |103-50| = 53 \) | 18.84%
3. (5,9,40,2) | \( |151-50| = 101 \) | 12.85%

*The sum of the multiplicative inverse of the fitness value:*
\[ 0.037037 + 0.009708 + 0.006623 = 0.053368 \]

**Father Chromosome | Mother Chromosome**

1. 3 | 2
2. 1 | 3
3. 3 | 1

### First Iteration

**Chromosome | Father Chromosome | Mother Chromosome | Offspring | Fitness Value | Likelihood**

1. (5,|9,40,2) | (7,|30,8,3) | (5,30,8,3) | \( |101-50| = 51 \) | 45.38%
2. (3,21,|4,5) | (5,9,|40,2) | (3,21,40,2) | \( |173-50| = 123 \) | 26.5%
3. (5,9,40,|2) | (3,21,4,|5) | (5,9,40,5) | \( |163-50| = 113 \) | 28.12%

*The sum of the multiplicative inverse of the fitness value:*
\[ 0.0099 + 0.005780 + 0.006134 = 0.021814 \]

**Father Chromosome | Mother Chromosome**

1. 1 | 2
2. 3 | 1
3. 2 | 3

### Second Iteration

**Chromosome | Father Chromosome | Mother Chromosome | Offspring | Fitness Value | Likelihood**

1. (5,|30,8,3) | (3,|21,40,2) | (5,21,40,2) | \( |175-50|=125 \) | 20.36%
2. (5,9,|40,5) | (5,30,|8,3) | (5,9,8,3) | \( |59-50|=9 \) | 60.38%
3. (3,21,40,|2) | (5,9,40,|5) | (3,21,40,5) | \( |185-50|=135 \) | 19.26%

*The sum of the multiplicative inverse of the fitness value:*
\[ 0.005714 + 0.016949 + 0.005405 = 0.028068 \]

**Father Chromosome | Mother Chromosome**

1. 1 | 3
2. 1 | 2
3. 2 | 3

### Third Iteration

**Chromosome | Father Chromosome | Mother Chromosome | Offspring | Fitness Value | Likelihood**

1. (5,|21,40,2) | (3,|21,40,5) | (5,21,40,5) | \( |187-50|=137 \) | 16.55%
2. (5,21,|40,2) | (5,9,|8,3) | (5,21,8,3) | \( |83-50|=33 \) | 37.28%
3. (5,9,8,|3) | (3,21,40,|5) | (5,9,8,5) | \( |67-50|=17 \) | 46.18%

*The sum of the multiplicative inverse of the fitness value:*
\[ 0.005347 + 0.012048 + 0.014925 = 0.03232 \]

### New Population

1. Chromosome 1 = (5,21,40,5)
2. Chromosome 2 = (5,21,8,3)
3. Chromosome 3 = (5,9,8,5)


![[Pasted image 20240702111404.png]]

### A* Search Path Analysis

**Nodes and Their Children:**

| Node  | Children                                         |
|-------|--------------------------------------------------|
| n     | o123, b3 (21), ts (31), o109 (36)                |
| b3    | b1 (21), b4 (29), ts (31), o109 (36)             |
| b1    | c2 (21), b2 (29), b4 (29), ts (31), o109 (36)    |
| c2    | c1 (21), b2 (29), b4 (29), c3 (29), ts (31), o109 (36) |
| c1    | b2 (29), b4 (29), c3 (29), ts (31), c3 (35), o109 (36) |
| c3    | b2 (29), b4 (29), ts (31), c3 (35), o109 (36)    |
| b2    | b4 (29), ts (31), c3 (35), b4 (35), o109 (36)    |
| b4    | ts (31), c3 (35), b4 (35), o109 (36), o109 (42)  |
| o109  | ts (31), c3 (35), b4 (35), o109 (42), o119 (51), o111 (55) |
| o119  | ts (31), c3 (35), b4 (35), o109 (42), o111 (55), o123 (53), storage (59) |
| o123  | ts (31), c3 (35), b4 (35), o109 (42), r123 (53), o125 (59), o111 (55), storage (59) |
| r123  | -                                                |

**A* Search Path:**
- o103 → b3 → b1 → c2 → c1 → c3 → b2 → b4 → o109 → o123 → r123

![[IMG_6155.jpeg]]

### Best-First Search Path

The best-first search path is: **S → A → C → B → H → I → L (Goal)**.

**Nodes and Their Children:**

|Node|Children|
|---|---|
|S|A (3), C (5), B (6)|
|A|C (5), B (6), E (8), D (9)|
|C|B (6), H (7), E (8), D (9)|
|B|H (7), E (8), D (9), F (12), G (14)|
|H|I (5), J (6), E (8), D (9), F (12), G (14)|
|I|L (0), K (1), M (2), J (6), E (8), D (9), F (12), G (14)|
|L|-|
