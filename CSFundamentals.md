# Computer Science Fundamentals

This document contains essential computer science fundamentals questions and answers. These explanations are designed to be clear and concise, helping technical recruiters understand core CS concepts when evaluating candidates.

## Data Structures and Algorithms

### 1. What is an algorithm?

**Answer:**
An algorithm is a step-by-step procedure or formula for solving a problem. It's a finite sequence of well-defined, computer-implementable instructions to accomplish a specific task. Key characteristics of algorithms include:

- Finiteness: Must terminate after a finite number of steps
- Definiteness: Each step must be precisely defined
- Input: May take zero or more inputs
- Output: Produces at least one output
- Effectiveness: Operations must be basic enough to be performed exactly

Examples include sorting algorithms (like quicksort), search algorithms (like binary search), and graph algorithms (like Dijkstra's shortest path).

### 2. What is time complexity and why is it important?

**Answer:**
Time complexity is a measure of the amount of time an algorithm takes to run as a function of the length of the input. It's typically expressed using Big O notation, which describes the upper bound of an algorithm's growth rate.

Time complexity is important because:
- It helps predict how an algorithm will perform with large inputs
- It allows comparison between different algorithms for the same problem
- It helps identify potential performance bottlenecks
- It guides algorithm selection based on specific requirements

Common time complexities (from fastest to slowest):
- O(1): Constant time (e.g., array access)
- O(log n): Logarithmic time (e.g., binary search)
- O(n): Linear time (e.g., linear search)
- O(n log n): Linearithmic time (e.g., efficient sorting algorithms like merge sort)
- O(n²): Quadratic time (e.g., simple sorting algorithms like bubble sort)
- O(2^n): Exponential time (e.g., recursive calculation of Fibonacci numbers)

### 3. What is space complexity?

**Answer:**
Space complexity is a measure of the amount of memory an algorithm uses relative to the size of the input. Like time complexity, it's typically expressed using Big O notation.

Space complexity includes:
- The memory needed for input data
- The memory needed for auxiliary variables and data structures
- The memory needed for the call stack in recursive algorithms

Understanding space complexity is important because:
- Memory is a limited resource
- Excessive memory usage can lead to performance issues or program crashes
- Some algorithms trade space for time (using more memory to run faster)
- In some environments (embedded systems, mobile devices), memory constraints may be strict

For example, an in-place sorting algorithm like quicksort has O(log n) space complexity due to the recursion stack, while merge sort typically has O(n) space complexity because it needs additional memory proportional to the input size.

### 4. What is the difference between a stack and a queue?

**Answer:**
Stacks and queues are both linear data structures, but they differ in how elements are added and removed:

**Stack:**
- Follows Last In, First Out (LIFO) principle
- Elements are added and removed from the same end (top)
- Main operations: push (add to top) and pop (remove from top)
- Real-world analogy: Stack of plates
- Use cases: Function call management, expression evaluation, undo mechanisms

**Queue:**
- Follows First In, First Out (FIFO) principle
- Elements are added at one end (rear) and removed from the other end (front)
- Main operations: enqueue (add to rear) and dequeue (remove from front)
- Real-world analogy: People waiting in line
- Use cases: Task scheduling, breadth-first search, print job management

Both data structures can be implemented using arrays or linked lists, and both have O(1) time complexity for their main operations when implemented correctly.

### 5. What is a linked list and what are its advantages and disadvantages?

**Answer:**
A linked list is a linear data structure where elements (nodes) are not stored in contiguous memory locations. Each node contains data and a reference (link) to the next node in the sequence.

**Advantages:**
- Dynamic size: Can grow or shrink during execution
- Efficient insertions/deletions: O(1) time if you have a reference to the node
- No pre-allocation of memory needed
- Efficient memory utilization (no need to reserve extra space)
- Easy implementation of stacks, queues, and other abstract data types

**Disadvantages:**
- Random access is not allowed: Must traverse from the beginning (O(n) time)
- Extra memory required for storing references/pointers
- Not cache-friendly due to non-contiguous memory allocation
- Reverse traversal is difficult in singly linked lists
- Higher memory overhead per element compared to arrays

Types of linked lists include:
- Singly linked list: Each node points to the next node
- Doubly linked list: Each node points to both next and previous nodes
- Circular linked list: Last node points back to the first node

### 6. What is a binary search tree?

**Answer:**
A binary search tree (BST) is a binary tree data structure with the following properties:

- Each node has at most two children (left and right)
- The left subtree of a node contains only nodes with keys less than the node's key
- The right subtree of a node contains only nodes with keys greater than the node's key
- Both the left and right subtrees are also binary search trees

These properties enable efficient searching, insertion, and deletion operations:
- Search: Start at the root and compare the target value. If equal, found. If less, go left. If greater, go right. Repeat until found or reach a leaf.
- Insert: Follow the search path until reaching a null reference, then add the new node there.
- Delete: More complex, involving cases for leaf nodes, nodes with one child, and nodes with two children.

In a balanced BST, these operations have O(log n) time complexity. However, in the worst case (when the tree becomes a linked list), they degrade to O(n).

Common balanced BST variants include AVL trees and Red-Black trees, which maintain balance through rotations.

### 7. What is a hash table and how does it work?

**Answer:**
A hash table (also called a hash map) is a data structure that implements an associative array, mapping keys to values. It uses a hash function to compute an index into an array of buckets or slots, from which the desired value can be found.

**How it works:**
1. A hash function converts the key into an integer (hash code)
2. The hash code is mapped to an index in the array (typically using modulo)
3. The key-value pair is stored at that index
4. To retrieve a value, the key is hashed again to find the index

**Collision handling:**
When two different keys hash to the same index, a collision occurs. Common strategies to handle collisions include:
- Chaining: Each bucket contains a linked list of entries
- Open addressing: If a collision occurs, look for the next available slot
  - Linear probing: Check the next slot sequentially
  - Quadratic probing: Check slots at quadratic intervals
  - Double hashing: Use a second hash function to determine the interval

**Performance:**
- Average case: O(1) for search, insert, and delete operations
- Worst case: O(n) if many collisions occur
- Space complexity: O(n)

Hash tables are widely used for implementing associative arrays, database indexing, caches, and sets.

### 8. What is recursion and when would you use it?

**Answer:**
Recursion is a programming technique where a function calls itself to solve a problem. A recursive function has two main components:

1. **Base case(s):** Condition(s) that stop the recursion
2. **Recursive case(s):** The function calling itself with a modified input that moves toward the base case

**When to use recursion:**
- When a problem can be broken down into smaller, similar subproblems
- When a problem has a naturally recursive structure
- When implementing algorithms like:
  - Tree or graph traversals
  - Divide and conquer algorithms (e.g., quicksort, merge sort)
  - Backtracking algorithms
  - Dynamic programming solutions
- When the solution is clearer and more elegant with recursion

**Advantages:**
- Can lead to cleaner, more readable code for certain problems
- Naturally models recursive structures and algorithms
- Reduces the need for complex nested loops

**Disadvantages:**
- Can lead to stack overflow errors if recursion is too deep
- Generally less efficient than iterative solutions due to function call overhead
- Higher memory usage due to the call stack
- Can be harder to trace and debug

Many recursive solutions can be rewritten iteratively, often with better performance but sometimes at the cost of code clarity.

### 9. What is dynamic programming?

**Answer:**
Dynamic programming is an algorithmic technique for solving complex problems by breaking them down into simpler overlapping subproblems and solving each subproblem only once, storing the results to avoid redundant calculations.

**Key characteristics:**
- Overlapping subproblems: Same subproblems are solved multiple times
- Optimal substructure: Optimal solution can be constructed from optimal solutions of subproblems

**Implementation approaches:**
1. **Top-down (Memoization):**
   - Recursive approach
   - Store results of subproblems in a table (usually a hash map)
   - Check if result is already calculated before computing

2. **Bottom-up (Tabulation):**
   - Iterative approach
   - Build a table from smallest subproblems to the original problem
   - Fill the table in a systematic way

**Classic examples:**
- Fibonacci sequence calculation
- Longest common subsequence
- Knapsack problem
- Matrix chain multiplication
- Shortest path algorithms (e.g., Floyd-Warshall)
- Edit distance

Dynamic programming is particularly useful for optimization problems where we need to find the best solution among many possible solutions.

### 10. What is the difference between a breadth-first search (BFS) and a depth-first search (DFS)?

**Answer:**
BFS and DFS are algorithms for traversing or searching tree or graph data structures.

**Breadth-First Search (BFS):**
- Explores all neighbors at the present depth before moving to nodes at the next depth level
- Uses a queue data structure (FIFO)
- Moves level by level, outward from the starting node
- Finds the shortest path in an unweighted graph
- Memory usage can be high as it needs to store all nodes at a level
- Good for finding the shortest path or when the solution is not far from the root

**Depth-First Search (DFS):**
- Explores as far as possible along each branch before backtracking
- Uses a stack data structure (LIFO) or recursion
- Goes deep into one path before exploring alternatives
- Memory usage is lower as it only needs to store the path from root to current node
- Good for maze problems, topological sorting, and when solutions are deep in the tree

**Implementation differences:**
- BFS: Uses a queue to keep track of nodes to visit next
- DFS: Uses a stack or recursion to keep track of nodes to visit next

**Time complexity:** Both are O(V + E) where V is the number of vertices and E is the number of edges
**Space complexity:** BFS is O(V), DFS is O(h) where h is the height of the tree or maximum depth of search