# Programming

This is a cheat sheet for programming (leetcode style) tests. It covers types of questions, algorithms and data structures.

## General Advice and Steps to Solve

- Really useful article on coding tests https://www.google.com/amp/s/www.freecodecamp.org/news/coding-interviews-for-dummies-5e048933b82b/amp/
- Readd the question outloud twice
- Write out the simplest example on paper! And then do one or two slightly more complex versions after that.
- Recursive 
    - What is one node needing for this, think one node at a time
- Test extreme versions of the input
- Coding Practice
    - Validate the input first
    - Consider the benefits of using hasmaps (hashmap + linked list are good for LRU cache implementation)
    - Try to avoid splitting or concatenating sequences (use start and end indices)
    - Sliding window technique is the key to lots of sequence problems
    - Array (can you sort it?)
    - Know how to convert numbers to binary in python
    - Whenever you see “top/lowest k”, think heap



## Question Types

### Arrays

- Running through the list once
- Using pointers to hold information in memory while rolling through once
- Examples
    - How many boats to carry people
    - Maximum water container
    - Longest substring

### Backtracking and Recursion

- Setting answer at the start and editing it as you go through
- Recursion on a method (that doesn’t return anything)
- Think about it from one nodes perspective
- Examples
    - What combinations of list elements sum to a target
    - Is a word on a board
    - Find all subsets of a list

### Dynamic Programming

- You save things as you go and reduce the problem into smaller and smaller parts
- Think “fibonacci sequence”. It’s recursive but you work from the end backwards, saving information as you go
- Always think, could this be done using stacks/queues instead (because this would likely be more efficient)?
- Example
    - Fibonacci sequence
    - Coin change that adds to amount
    - Unique number of paths

### Hash Tables and Maps

- Often about finding duplicates
- Example
    - Does this list contain duplicates?
    - Given an array of strings, group the anagrams together
    - Of these 4 list, what combination of elements sum to 0?

### LinkedList

- These will always contain a linked list (pointers)
- Using pointers is often the best way to do these problems
- Examples
    - Remove the nth node from the list
    - Odd/even linked list

### Maths

- These probably won’t come up, but they are problems that can be solved using a mathematical formula
- Examples
    - Count primes
    - Missing number
    - Single number

### Stacks and Queues

- These might about traversing a tree and storing ALL the values in it and return them in some order
- Examples
    - Valid parentheses
    - Binary tree
    - Level order traversal
    - Post order traversal
    - Zigzag level traversal

### Trees

- You can normally tell if this isn’t a stacks/queues problem because it is asking about one specific element of the tree
- It’ll usually involve some kind of recursion
- Examples
    - Kth smallest element of a binary tree
    - Is the tree symmetrical
    - Path sum in the tree

## Big-O Notation

An algorithm is better than another one if it takes less time and space

### Basic Form

- Count how many operation you have e.g addition, multiplication, division, comparison, assignments (of values to variables)
- O(1) (constant complexity)
    - The number of operations in the algorithm does not depend on the size of the array
    - The number of iterations is always the same no matter how big N is
    - E.g. a simple equation like len(N)*len(N+1) / 2
- O(N) (linear complexity)
    - The number of operations in the algorithm increases linearly with the size of the array
    - E.g. a loop e.g. [n+n for n in N]
    - Or even two loops one after the other (but NOT embedded loops)
- O(N^c) (quadratic complexity)
    - The number of operations in the algorithm increase quadratically with the size of the array
    - E.g. a loop inside a loop would be O(N^2) e.g. [n+m for m in N for n in N]
    - E.g. a loop inside a loop inside a loop would be O(N^3)

### Simplifying Big-O Notations

- Ignore constants
    - O(constant) = O(1)
    - O(aN+b) = O(N)
- Ignore the smaller terms
    - O(aN^2 + bN) = O(N^2)

### Complexity of Standard Operations

- Arithmetic operations and assignments are constants
- Direct array element access (by index) is a constant

### Big-O Space Complexity

When you are analysing space complexity, you only care about the space your algorithm takes, not the space the input takes.

- O(1)
    - When the amount of space required doesn’t depend on the size of the input
    - E.g. assigning two variables e.g.

```
sum=0; 
n=len(arr);
Loop as i from (0, n):
	sum+=arr[i]
return sum
```

- O(N)
    - The amount of space required scales linearly with the input e.g.
```
arr = [n for n in N]
```

- Space Complexity of Popular Data Structures
    - Hash Tables, Stacks, Queues, String and Arrays: O(N). This is because the number of slots required to store a hash map scales with the number of elements that need to be stored
    - Say you had 2 inputs N and M, and you wanted to create a 2D array for these elements, then the space complexity of this would be O(NM)

- Logarithms
    - Log(N) is better than N
    - NLog(N) is better than N^2
    - NLog(N) is worse than N
    - Binary Search has a time complexity of Log(N) which makes it one of the most popular search algorithms out there
    - Merge Sort (NLog(N))

## Algorithms

### Binary Search

Only works on sorted arrays

### Breadth First Search

```
BFS (G, s) //Where G is the graph and s is the source node
      let Q be queue.
      Q.enqueue( s ) //Inserting s in queue until all its neighbour vertices are marked.

      mark s as visited.
      while ( Q is not empty)
           //Removing that vertex from queue,whose neighbour will be visited now
           v  =  Q.dequeue( )

          //processing all the neighbours of v  
          for all neighbours w of v in Graph G
               if w is not visited 
                        Q.enqueue( w )             //Stores w in Q to further visit its neighbour
                        mark w as visited.
```

### Depth First Search

```
procedure DFS(G, v) is
    label v as discovered
    for all directed edges from v to w that are in G.adjacentEdges(v) do
        if vertex w is not labeled as discovered then
            recursively call DFS(G, w)
```

## Data Structures

### Hash Tables

Hashing is generating a value from a string using some sort of mathematical function.

A good hash function is:
- Uniform
- Easy to compute
- Avoids collisions

Find something in a hash table is O(1) because you just have to has the value and therefore you can figure out where it is in the table (and this hashing function doesn’t rely on the number of elements in the hash table)
Collision Handling
- Chaining: Make each cell of the hash table point to a linked list
- Open addressing: 
    - The values are stored in the hash table itself
    - If the key is available then insert the item into that cell
    - If the key is not available then probe for an available cell
    - Probing techniques
        - Linear probing (you look at the next slot)
        - Quadratic probing
        - Double hashing
Comparisons of collision handling
- Chaining
    - Simple to implement
    - The hash table is never full
    - Cache performance is not good
    - Users extra space to store lists
    - Usually used when number of keys is unknown
- Open Addressing
    - Requires more computation
    - Hash tables can get full
    - Open addressing provides better cache performance
    - No extra space required
    - Mostly used when the frequency and number of keys is known

### Linked Lists

- Two types
    - Singly linked list
        - Each node has one pointer to the next node
    - Doubly linked list
        - Each node has two pointers, to the next node and to the previous node
- Head is first node, tail is the last element
- Each element is linked to the next element
- Disadvantages (compared to array)
    - O(n) searching (sorted or not, it is the same)
- Advantage
    - Insertions and deletions are easier

### Stacks

- Last in First Out (LIFO)
- Real life example: Stack of plates
- Time complexity
    - Pop, Push and Top are all O(1)

### Queues

- First in First Out (FIFO)
- Real life example: queue of people
- Time Complexity
    - Enqueue,  Dequeue, Front are all O(1)

### Graphs

Types of graphs
- Undirected graph means all the edges are bidirectional
- Directed graph means the edges have a direction
- Weighted graph: each edge is assigned a weight or a cost
- Cyclic graph: they contain at least one graph cycle

### Trees

- They a really important for interviews and for computer science in general so study them well
- They are a connected undirected acyclic graph
- M-ary tree
    - Every internal vertex of the tree has no more than m children
- Binary tree
    - Every vertex has at most 2 children
    - Balanced binary tree is a tree in which the depth of the two subtrees of every node never differ by more than 1
    - Unbalanced binary tree are the opposite of the above
- In-order traversal is traversed in this order LEFT-ROOT-RIGHT
- Pre-order traversal is traversed in this order ROOT-LEFT-RIGHT
- Post-order traversal is traversed in this order LEFT-RIGHT-ROOT

### Dynamic Programming

- Is the process of dividing a problem into subproblems and then saving the results of these sub-problems to be used later
- A problem is a DP problem if
    - It is a recursive problem
    - It has a lot of repeated states
- We are trading memory for speed
- There are two approaches
    - Top down
    - Bottom up
