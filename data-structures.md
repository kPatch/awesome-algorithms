# Data Structures

## Table of Contents
- [Binary Trees](#binary-trees)
- [Red Black Trees](#red-black-trees)

## Binary Trees
Also known as Heaps.

### Definitions

- **Full Binary Tree**: Has mixum number of nodes
- **Complete Binary Tree**: It's a full binary tree up to (*h -1*) and where all the nodes in *h* are as far left as possible

### Implementation
We can implement a binary tree in an array, where
- index *i* is the index of the a given node
- parent of *i* is in: *floor(i/2)*
- left-child of *i* is in: *2 \* i*
- right-child of *i* is in: *2 \* i + 1*

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
