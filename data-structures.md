# Data Structures

## Table of Contents
- [Binary Trees](#binary-trees)
- [Heap](#heap)
- [Binary Search Trees](#binary-search-trees)
- [Red Black Trees](#red-black-trees)
- [Sets](#sets)

## Binary Trees
Also known as Heaps.

### Definitions

- **Full Binary Tree**: Has mixum number of nodes
- **Complete Binary Tree**: It's a full binary tree up to (*h -1*) and where all the nodes in *h* are as far left as possible

### Formalism
- Let *n* be the number of nodes in the tree
- Let *h* be the height of the tree
- Let *d* be the depth of a given node or tree

### Overview
- The maximum number of nodes at a given height *h_i* is (*2^h_1*)
  - For example, the maximum number of nodes at height 2 is *2^2*, which is 4
- The minimum height *(h_min)* of a tree is *floor(log_base2(n))*
- The maximum height *(h_max)* of a tree is *n-1*

### Implementation
We can implement a binary tree in an array, where
- index *i* is the index of the a given node
- parent of *i* is in: *floor(i/2)*
- left-child of *i* is in: *2 \* i*
- right-child of *i* is in: *2 \* i + 1*

## Heap
A binary heap is a **complete binary tree**  which satisfies the heap ordering property. There are two types of ordering properties:
- the **min-heap property:** the value of each node is greater than or equal to the value of its parent, with the minimum-value element at the root
- the **max-heap property:** the value of each node is less than or equal to the value of its parent, with the maximum-value element at the root.

The latter is the reason why heaps are data structures often used to represent **priority queues** - a heap is a useful data structure when you need to remove the object with the highest (or lowest) priortiy.   

One thing to note, again, is that a heap is a **complete binary tree**. Meaning that it's a full binary tree at least up to (*h -1*) -  that height *h-1* has all possible node. At heigh *h*, all the nodes are as far left as possible.   

Since a heap is a complete binary tree, it has a smallest possible height - a heap with *N* nodes always has *O(log n)* height.



### References
- [CMU - Binary Heaps](https://www.cs.cmu.edu/~adamchik/15-121/lectures/Binary%20Heaps/heaps.html)

## Binary Search Trees

### Property   
Let *u*, *v*, *w* be three nodes such that *u* is in the left subtree of *v* and *w* is in the right subtree of *v*.   
They must satisfy the following property:   
- *key(u) <= key(v) <= key(w)*

### Binary Search
- In worst case, takes *O(n)* when the tree is imbalanced / skewed
- In best case, takes *O(log n)* when the tree is balanced (either a full or tree)

### References
- [GeeksforGeeks - BST, AVL Complexity](https://www.geeksforgeeks.org/complexity-different-operations-binary-tree-binary-search-tree-avl-tree/)

## Red Black Trees
Red Black Trees are self-balancing Binary Search Trees (BST)

### The Rules
1. Every node is either RED or BLACK
2. The **root** is always BLACK, if not BLACK we make it / force it to be black
3. New insertions are always RED
4. Every path from root to leaf has the **same number of BLACK nodes** (RED is ok)
5. No path can have two consecutive RED nodes (can have consecutive BLACK nodes)
6. NULLS are considered BLACK

## Rebalancing
1. Black Aunt Rotate (BAR)
2. Read Aunt Color Flip (recolor parent and grandparent)

### Left Child's Left Subtree (LL)
If the imbalance takes place in the left child's left subtreet we do a **right rotation** on the **granparent**

### Right Child's Right Subtree (RR)
If the imbalance takes place in the right child's right subtree we do a **left rotation** on the **granparent**

### Right Child's Left Subtree (RL)
If the imbalance takes place in the right child's left subtree we do a **right, left rotation**.   
- Right rotation of the parent of the problematic node
- Left rotation of the grandparent

### Left Child's Right Subtree (LR)
If the imbalance takes place in the left child's right subtree we do a **left, right rotation**.   
- Left rotation of the parent of the problematic node
- Right rotation of the grandparent

## Sets
In mathematics, a set is a well-defined collection of distinct objects, considered as an object in its own right. For example, the numbers 2,4, and 6 are distinct objects when considered separately, but when they are considered collectively they form a single set of size three, written ***{2, 4, 6}***.

### References
- [TutorialEndge](https://tutorialedge.net/compsci/data-structures/sets-for-beginners/)
- [Benoit Vallon](https://blog.benoitvallon.com/data-structures-in-javascript/the-set-data-structure/)
- [Wiki - Sets (Abstract Data Type)](https://en.wikipedia.org/wiki/Set_(abstract_data_type))
