# Data Structures

## Table of Contents
- [Stacks](#stacks)
- [Queues](#queues)
- [Binary Trees](#binary-trees)
- [Binary Heap](#binary-heap)
- [Binary Search Trees](#binary-search-trees)
- [Red Black Trees](#red-black-trees)
- [Sets](#sets)

## Stacks
Stacks follow Last In First Out (LIFO) scheme. Meaning that new items are *pushed* (inserted) at the top of the stack, and *popping* (removing) the stack returns the last item that was *pushed*.   
When you think about stacks, you can think about stacking a set of plates. You begin stacking one plate at a time. To begin washing the plates, you must start by removing a plate from the top of the stack.   

### Operations
- ***push()*** - inserts an element
- ***pop()*** - removes and returns the last inserted element

### Applications
- Overall, a stack can be used for backtracking. The process, where you need to access the most recent data elements in a series of elements. Think of a labyrinth or maze. You can explore and keep track of the places you've visited. Once you hit a dead end, you must backtrack to the previouce choice point.
- Think of a browser history. You 'pop' the last item from the history stack by pressing the 'back' button.
- **Depth-first search** with a Stack. This is in reference to backtracking. You go down a path until we get a dead end (a leaf in a tree), then we backtrack or back up (by popping a stack) to get to an alternative path (where there are other children in a tree to visit).

### Implementations
**Array-based Stack**   
You can implement a Stack by using an array. An empty stack is an empty array, where a pointer *i* points to index 0. When an item is pushed into the stack, the pointer is incremented by 1 (*i + 1*). When an item is popped from the stack, the item at index *i* is returned and the index is decremented (*i - 1*).

If the stack becomes empty (index isless than 0), we can throw an *EmptyStackException*.   
In a stack-based implementation, the stack may throw an *FullStackException* to indicate that the underlying array has become full. **NOTE** that this is a limitation of an array-based implementation.   

**NOTE** that we may implement a doubling strategy, where the size of the underlying array is doubled. When considering the long-term use of this strategy, the amortized cost of a push is *O(1)*.   

### References
- [CMU - Stacks and Queues](https://www.cs.cmu.edu/~adamchik/15-121/lectures/Stacks%20and%20Queues/Stacks%20and%20Queues.html)

## Queues

### References
- [CMU - Stacks and Queues](https://www.cs.cmu.edu/~adamchik/15-121/lectures/Stacks%20and%20Queues/Stacks%20and%20Queues.html)

## Binary Trees
Look at [Binary Heaps](#binary-heap).

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

```
Tree Representation

                A   
            /       \
          C           B
        /   \       /   \
      D      G    F       K
     / \    /
    H   E  J
```

| 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 |
|---|:-:|--:|--:|--:|--:|--:|--:|--:|--:|---:|
|   | A | C | B | D | G | F | K | H | E | J  |

## Binary Heap
A binary heap is a **complete binary tree**  which satisfies the heap ordering property. There are two types of ordering properties:
- the **min-heap property:** the value of each node is greater than or equal to the value of its parent, with the minimum-value element at the root
- the **max-heap property:** the value of each node is less than or equal to the value of its parent, with the maximum-value element at the root.

The latter is the reason why heaps are data structures often used to represent **priority queues** - a heap is a useful data structure when you need to remove the object with the highest (or lowest) priortiy.   

One thing to note, again, is that a heap is a **complete binary tree**. Meaning that it's a full binary tree at least up to (*h -1*) -  that height *h-1* has all possible node. At heigh *h*, all the nodes are as far left as possible.   

Since a heap is a complete binary tree, it has a smallest possible height - a heap with *N* nodes always has *O(log n)* height.

### Implementation

We can implement a binary tree in an array, where
- index *i* is the index of the a given node
- parent of *i* is in: *floor(i/2)*
- left-child of *i* is in: *2 \* i*
- right-child of *i* is in: *2 \* i + 1*

```
Consider the folowing binary heap representation
                6   
            /       \
          7           12
        /   \       /   \
     10      15   17      
```

| 0 | 1 | 2 | 3  | 4  | 5  | 6  | 7  |
|---|:-:|--:|---:|---:|---:|---:|---:|
|   | 6 | 7 | 12 | 10 | 15 | 17 |    |

### Insert
The insertion process is as follows:
- Append the new element at the end of the heap (as the last element of the array)
- Repair the heap property by (1) comparing the added element with its parent and (2) moving the added element up a level. That is, swapping positions with the parent when needed. This process is called **percolation up** or also known as **upheap**
- The comparison is repeated until the new element reaches the root, or a node whose parent has a key smaller than or equal to the new element

Consider the following example of adding the element ***5***


```
Insert 5 at the end of the heap.
                6   
            /       \
          7           12
        /   \       /   \
     10      15   17     (5)
```


| 0 | 1 | 2 | 3  | 4  | 5  | 6  |   7   |
|---|:-:|--:|---:|---:|---:|---:|------:|
|   | 6 | 7 | 12 | 10 | 15 | 17 | **5** |

```
RESTORE HEAP PROPERTY
Compare with parent (k/2). 5 < 12 is true.
New element is less than parent, swap.
                6   
            /       \
          7          (5)
        /   \       /   \
     10      15   17     12
```


| 0 | 1 | 2 |   3   | 4  | 5  | 6  | 7  |
|---|:-:|--:|------:|---:|---:|---:|---:|
|   | 6 | 7 | **5** | 10 | 15 | 17 | 12 |



```
RESTORE HEAP PROPERTY
Compare with parent (k/2). 5 < 6 is true.
New element is less than parent, swap.
The new element has reached the root.
               (5)   
            /       \
          7           6
        /   \       /   \
     10      15   17     12
```


| 0 |   1   | 2 | 3 | 4  | 5  | 6  | 7  |
|---|:-:|--:|------:|---:|---:|---:|---:|
|   | **5** | 7 | 5 | 10 | 15 | 17 | 12 |

Because in the worst case scenario the new element will have to percolate up to the root, the worst-case runningg time of the algorithm is ***O(log n)*** -  which is the height of a tree.

### Remove Min
The minimum (or maximum in max heap) can be found at the root
The removal algorithm consists of the following steps:
1. Replace the root element with the last element (the element at the end of the array).
2. Restore the heap property by ***percolating*** down.

Similar to insertion, the worst-case runtime is ***O(log n)***.

### Building Heap Bottom-up

Time complexity is ***O(n)**. Look at the following [reference](https://stackoverflow.com/questions/9755721/how-can-building-a-heap-be-on-time-complexity).

### References
- [CMU - Binary Heaps](https://www.cs.cmu.edu/~adamchik/15-121/lectures/Binary%20Heaps/heaps.html)
- [StackOverflow - How can building a heap be O(n) time complexity?](https://stackoverflow.com/questions/9755721/how-can-building-a-heap-be-on-time-complexity)
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
