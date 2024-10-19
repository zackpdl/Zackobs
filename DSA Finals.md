## Graph Traversal Algorithms: BFS and DFS

**Breadth-First Search (BFS):**

- **Concept:** Explores all adjacent vertices of a vertex before moving to the next vertex.
- **Data structure:** Queue.
- **Steps:**
    1. Visit the starting vertex.
    2. Add adjacent vertices to the queue.
    3. Repeat until the queue is empty.
- **Traversal order:** Level-order traversal on a binary tree.

**Depth-First Search (DFS):**

- **Concept:** Explores one branch of the graph as deeply as possible before backtracking.
- **Data structure:** Stack.
- **Steps:**
    1. Visit the starting vertex.
    2. Push adjacent vertices onto the stack.
    3. Repeat until the stack is empty.
- **Traversal order:** Pre-order traversal on a binary tree.

**Key Points:**

- Both BFS and DFS can be used to explore graphs.
- BFS is suitable for finding shortest paths in unweighted graphs.
- DFS is suitable for detecting cycles and finding connected components.
- The choice between BFS and DFS depends on the specific problem and the desired outcome.

**Example:**

```
Graph:

1 -- 2 -- 3
|  |  |
4 -- 5 -- 6

BFS traversal: 1, 2, 4, 3, 5, 6
DFS traversal: 1, 2, 3, 6, 5, 4
```

**Time Complexity:**

- Both BFS and DFS have a time complexity of O(V + E), where V is the number of vertices and E is the number of edges in the graph.  
    

**Additional Notes:**

- You can use different starting vertices for BFS and DFS.
- The traversal order may vary depending on the implementation and the order of adjacent vertices.
- BFS and DFS can be modified for specific applications, such as finding shortest paths in weighted graphs or detecting cycles in directed graphs.

**Practice Problems:**

- Implement BFS and DFS algorithms.
- Solve graph traversal problems using BFS and DFS.
- Analyze the time and space complexity of BFS and DFS for different graph structures.

# Prims n Kruskals

**Spanning Tree:** A subgraph of a graph that connects all vertices with the minimum possible number of edges.

**Minimum Cost Spanning Tree (MST):** A spanning tree where the sum of the weights of the edges is minimum.

**Finding MSTs:**

- **Brute Force:** Try all possible spanning trees and find the one with the minimum cost. (Not efficient for large graphs)
- **Greedy Algorithms:**
    - **Prim's Algorithm:**
        1. Start with a single vertex.
        2. Add the minimum-weight edge connected to the current set of vertices.
        3. Repeat until all vertices are included.
    - **Kruskal's Algorithm:**
        1. Sort edges by weight.
        2. Add edges to the MST if they don't create a cycle.

**Prim's Algorithm:**

- **Time complexity:** O(E log V) using a min-heap.
- **Suitable for dense graphs.**

**Kruskal's Algorithm:**

- **Time complexity:** O(E log E) using efficient sorting algorithms.
- **Suitable for sparse graphs.**

**Key Points:**

- MSTs are unique for a given graph.
- The cost of an MST is the minimum possible cost among all spanning trees.
- Prim's and Kruskal's algorithms are efficient for finding MSTs.
- The choice between Prim's and Kruskal's depends on the graph structure and implementation considerations.

**Example:**

```
Graph:

1 -- 2 (weight 5)
|  |
3 -- 4 (weight 3)
|  |
5 -- 6 (weight 6)

MST:

1 -- 2 (weight 5)
|  |
3 -- 4 (weight 3)
|
5 (weight 6)

Cost of MST: 14
```

# Dijkstra's algorithm 

**1. Initialization:**

- Choose a starting vertex (source) and assign it a distance of 0.
- Assign all other vertices a distance of infinity.
- Create a priority queue to store vertices based on their current distance estimates.
- Initialize the priority queue with the source vertex and its distance.

**2. Algorithm:**

While the priority queue is not empty:

1. Extract the vertex with the minimum distance from the priority queue.
2. Mark the extracted vertex as visited.
3. Update the distances of all neighbors of the extracted vertex that are not yet visited. If a shorter path is found, update the distance and add the vertex to the priority queue.

**Example:**

```
Graph:
   1 -- 2 (weight 4)
   |  |
   3 -- 4 (weight 3)
   |  |
   5 -- 6 (weight 6)

Dijkstra's Algorithm:

1. Initialize:
   * Source vertex: 1
   * Distances: [0, inf, inf, inf, inf, inf]
   * Priority queue: [(1, 0)]

2. While priority queue is not empty:
   2.1. Extract vertex with minimum distance: 1
   2.2. Mark vertex 1 as visited.
   2.3. Update neighbors of 1:
       * Update distance of vertex 2 to 4 (if it was infinity before).
       * Add vertex 2 to priority queue with distance 4.
   2.4. Update neighbors of 2:
       * Update distance of vertex 3 to 7 (if it was infinity before).
       * Add vertex 3 to priority queue with distance 7.

3. While priority queue is not empty:
   3.1. Extract vertex with minimum distance: 3
   3.2. Mark vertex 3 as visited.
   3.3. Update neighbors of 3:
       * Update distance of vertex 4 to 10 (if it was infinity before).
       * Add vertex 4 to priority queue with distance 10.

4. While priority queue is not empty:
   4.1. Extract vertex with minimum distance: 2
   4.2. Mark vertex 2 as visited.
   4.3. Update neighbors of 2:
       * Update distance of vertex 5 to 11 (if it was infinity before).
       * Add vertex 5 to priority queue with distance 11.

5. While priority queue is not empty:
   5.1. Extract vertex with minimum distance: 4
   5.2. Mark vertex 4 as visited.

6. While priority queue is not empty:
   6.1. Extract vertex with minimum distance: 5
   6.2. Mark vertex 5 as visited.
   6.3. Update neighbors of 5:
       * Update distance of vertex 6 to 17 (if it was infinity before).
       * Add vertex 6 to priority queue with distance 17.

7. While priority queue is not empty:
   7.1. Extract vertex with minimum distance: 6
   7.2. Mark vertex 6 as visited.

**Shortest Paths:**

* The shortest path from 1 to 1 is 0.
* The shortest path from 1 to 2 is 4.
* The shortest path from 1 to 3 is 7.
* The shortest path from 1 to 4 is 10.
* The shortest path from 1 to 5 is 11.
* The shortest path from 1 to 6 is 17.

**Visualization:**

```

```
    1
  /   \
 4     2
  \   /
    3
    |
    5
    |
    6
```

```

**Key Points:**

* The algorithm maintains a set of visited vertices and a priority queue of unvisited vertices with their current distance estimates.
* At each step, it selects the vertex with the minimum distance from the priority queue and updates the distances of its unvisited neighbors.
* The algorithm terminates when all vertices have been visited or the priority queue is empty.
* The shortest path to any vertex can be found by tracing back from that vertex to the source vertex using the parent pointers stored in each vertex.

I hope this example helps you understand Dijkstra's algorithm better!
```

# Disjoint Sets

**Disjoint Sets** are collections of non-overlapping sets. They are often used in algorithms and data structures to represent relationships between elements.

**Key Operations:**

1. **Make-Set(x):** Creates a new set containing only the element x.
2. **Union(x, y):** Unites the sets containing elements x and y.
3. **Find-Set(x):** Returns the representative of the set containing x.

**Representations:**

- **Linked Lists:** Each set is represented as a linked list. The representative is the head of the list.
- **Trees:** Each set is represented as a rooted tree. The representative is the root.

**Union by Rank:**

- To optimize Union, we maintain the rank of each tree (an estimate of its height).
- When merging two sets, the root of the smaller rank tree becomes the child of the root of the larger rank tree.

**Path Compression:**

- To optimize Find, we perform path compression. During Find, we make all nodes on the path to the root direct children of the root.

**Time Complexity:**

- **Amortized time complexity:** O(α(n)) per operation, where α(n) is the inverse Ackermann function.

**Applications:**

- **Minimum Spanning Trees:** Kruskal's algorithm uses disjoint sets to detect cycles.
- **Connected Components:** Finding connected components in a graph.
- **Cycle Detection:** Detecting cycles in undirected graphs.

**Example:**

```
Graph:

1 -- 2
|  |
3 -- 4

Disjoint Sets:

Set 1: {1, 2}
Set 2: {3, 4}

Union(1, 3):

Set 1: {1, 2, 3, 4}
```

**Key Points:**

- Disjoint sets are efficient for representing sets and performing Union and Find operations.
- Union by rank and path compression are essential for optimizing performance.
- Disjoint sets have various applications in graph algorithms and data structures.


# Here's how to create Edge Lists, Adjacency Lists, and Adjacency Matrices from a graph:

**1. Edge Lists**

**1.1. Unweighted Graph:**

1. Create an empty list called `edges`.
2. For each edge in the graph, add a tuple `(vertex_1, vertex_2)` to the `edges` list.

**Example:**

```
Graph:
   1 -- 2
   |  |
   3 -- 4

Edge List: [(1, 2), (2, 3), (3, 4)]
```

**1.2. Weighted Graph:**

1. Create an empty list called `edges`.
2. For each edge in the graph, add a tuple `(vertex_1, vertex_2, weight)` to the `edges` list.

**Example:**

```
Graph:
   1 -- 2 (weight 5)
   |  |
   3 -- 4 (weight 3)

Edge List: [(1, 2, 5), (2, 3, 7), (3, 4, 2)]
```

**2. Adjacency Lists**

**2.1. Unweighted Graph:**

1. Create a list called `adj` with `num_vertices` empty lists.
2. For each edge in the graph, add the neighbor vertex to the corresponding index in `adj`.
3. For undirected graphs, add the reverse edge as well.

**Example:**

```
Graph:
   1 -- 2
   |  |
   3 -- 4

Adjacency List: [[2], [1, 3], [2, 4], [3]]
```

**2.2. Weighted Graph:**

1. Create a list called `adj` with `num_vertices` empty lists.
2. For each edge in the graph, add a tuple `(neighbor_vertex, weight)` to the corresponding index in `adj`.
3. For undirected graphs, add the reverse edge with the same weight.

**Example:**

```
Graph:
   1 -- 2 (weight 5)
   |  |
   3 -- 4 (weight 3)

Adjacency List: [[(2, 5)], [(1, 5), (3, 2)], [(2, 7), (4, 2)], [(3, 2)]]
```

**3. Adjacency Matrices**

**3.1. Unweighted Graph:**

1. Create a 2D matrix `adj` with `num_vertices` rows and columns.
2. Initialize all elements of `adj` to `0`.
3. For each edge in the graph, set the corresponding element in `adj` to `1`.
4. For undirected graphs, set the corresponding element in the transposed matrix to `1`.

**Example:**

```
Graph:
   1 -- 2
   |  |
   3 -- 4

Adjacency Matrix:
[[0, 1, 0, 0],
 [1, 0, 1, 0],
 [0, 1, 0, 1],
 [0, 0, 1, 0]]
```

**3.2. Weighted Graph:**

1. Create a 2D matrix `adj` with `num_vertices` rows and columns.
2. Initialize all elements of `adj` to `0`.
3. For each edge in the graph, set the corresponding element in `adj` to the weight of the edge.
4. For undirected graphs, set the corresponding element in the transposed matrix to the weight of the edge.

**Example:**

```
Graph:
   1 -- 2 (weight 5)
   |  |
   3 -- 4 (weight 3)

Adjacency Matrix:
[[0, 5, 0, 0],
 [5, 0, 7, 0],
 [0, 7, 0, 2],
 [0, 0, 2, 0]]
```

**Visualizing Graphs:**

You can visualize graphs using various tools and libraries. Some popular options include:

- **NetworkX:** A Python library for graph analysis and visualization.
- **Gephi:** A standalone software for visualizing large graphs.
- **Matplotlib:** A Python library for plotting and visualization, which can be used to create basic graph visualizations.