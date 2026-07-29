---
title: Algorithms
---

## **1. Searching Algorithms**

| Algorithm | Description |
|---|---|
| Linear Search | Checks each element one by one until the target is found |
| Binary Search | Halves the search range each step on a sorted array |
| Jump Search | Jumps ahead by fixed steps, then does linear search |
| Interpolation Search | Estimates position using value distribution for faster search |
| Exponential Search | Finds range exponentially, then applies binary search |

## **2. Sorting Algorithms**

| Algorithm | Description |
|---|---|
| Bubble Sort | Repeatedly swaps adjacent elements if they are in wrong order |
| Selection Sort | Selects the minimum and places it at the correct position |
| Insertion Sort | Builds sorted array by inserting each element in its place |
| Merge Sort | Divides array in half, sorts each, then merges |
| Quick Sort | Partitions array around a pivot and recursively sorts |
| Heap Sort | Builds a heap, then repeatedly extracts the max/min |
| Counting Sort | Counts occurrences and reconstructs sorted array |
| Radix Sort | Sorts digit by digit from least to most significant |
| Bucket Sort | Distributes elements into buckets and sorts each |
| Shell Sort | Generalization of insertion sort using gap sequences |

## **3. Recursion and Backtracking**

| Algorithm | Description |
|---|---|
| Recursion | Solves a problem by calling itself with a smaller input |
| N-Queens Problem | Places N queens on a board with no two attacking each other |
| Sudoku Solver | Fills a 9x9 grid satisfying row, column, and box constraints |
| Rat in a Maze | Finds a path from start to end through a maze |
| Hamiltonian Path | Finds a path visiting every vertex exactly once |

## **4. Divide and Conquer**

| Algorithm | Description |
|---|---|
| Merge Sort | Splits and merges sorted halves |
| Quick Sort | Partitions around pivot and conquers each part |
| Binary Search | Divides search space in half each step |
| Closest Pair Problem | Finds closest pair of points using divide and conquer |

## **5. Greedy Algorithms**

| Algorithm | Description |
|---|---|
| Activity Selection | Selects max non-overlapping activities by earliest end time |
| Huffman Coding | Builds optimal prefix-free code using frequency |
| Fractional Knapsack | Picks items by value/weight ratio to maximize value |
| Prim's Algorithm | Builds minimum spanning tree by adding cheapest edges |
| Kruskal's Algorithm | Builds MST by sorting edges and avoiding cycles |
| Dijkstra's Algorithm | Finds shortest path from source using greedy relaxation |

## **6. Dynamic Programming (DP)**

| Algorithm | Description |
|---|---|
| Fibonacci Series | Classic memoized recursion to compute nth Fibonacci number |
| Longest Common Subsequence (LCS) | Finds the longest sequence common to two strings |
| Longest Increasing Subsequence (LIS) | Finds longest subsequence in strictly increasing order |
| 0/1 Knapsack | Maximizes value selecting items within weight limit |
| Matrix Chain Multiplication | Finds optimal order to multiply a chain of matrices |
| Coin Change Problem | Finds minimum coins to make a target amount |

## **7. Graph Algorithms**

| Algorithm | Description |
|---|---|
| Breadth First Search (BFS) | Explores graph level by level using a queue |
| Depth First Search (DFS) | Explores as far as possible along each branch using a stack |
| Dijkstra's Algorithm | Shortest path from source in weighted graph (no negatives) |
| Bellman-Ford Algorithm | Shortest path handling negative weights |
| Floyd-Warshall Algorithm | All-pairs shortest paths in O(V³) |
| Prim's Algorithm | Greedy MST by expanding nearest unvisited vertex |
| Kruskal's Algorithm | MST by sorting edges and using Union-Find |
| Topological Sort | Linear ordering of vertices in a DAG |
| Tarjan's Algorithm | Finds strongly connected components in O(V+E) |

## **8. String Algorithms**

| Algorithm | Description |
|---|---|
| KMP (Knuth-Morris-Pratt) | Pattern matching without backtracking using failure function |
| Rabin-Karp | Pattern matching using rolling hash |
| Z Algorithm | Computes Z-array for pattern matching in O(n) |
| Boyer-Moore | Right-to-left pattern matching with skip heuristics |
| Aho-Corasick | Multi-pattern matching using a trie and failure links |

## **9. Bit Manipulation Algorithms**

| Algorithm | Description |
|---|---|
| XOR Operations | Cancels duplicates; used in finding missing/single numbers |
| Bit Masking | Isolates, sets, or clears specific bits using AND/OR/XOR |
| Fast Exponentiation | Computes a^b in O(log b) using repeated squaring |
| Counting Set Bits | Counts number of 1-bits using Brian Kernighan's method |

## **10. Mathematical Algorithms**

| Algorithm | Description |
|---|---|
| Euclidean GCD | Computes greatest common divisor using repeated modulo |
| Sieve of Eratosthenes | Finds all primes up to N in O(n log log n) |
| Prime Factorization | Decomposes a number into its prime factors |
| Modular Arithmetic | Performs operations under a modulus to prevent overflow |
| Fast Power | Computes modular exponentiation in O(log n) |

## **11. Advanced Algorithms**

| Algorithm | Description |
|---|---|
| Branch and Bound | Explores solution space with pruning for optimization |
| Network Flow Algorithms | Finds maximum flow through a flow network |
| Maximum Bipartite Matching | Finds largest matching in a bipartite graph |
| Computational Geometry Algorithms | Solves geometric problems like convex hull and intersection |
| Randomized Algorithms | Uses randomness to improve average-case performance |
