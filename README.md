<h3 align="center"> Irvin's Awesome Review / List of Algorithm Resources</h3>
<p align="center"> ༼ つ ◕_◕ ༽つ</p>

## Contents

- [About](#about)
- [Amortized Analysis](#amortized-analysis)
- [Parallel Algorithms](#parallel-algorithms)

## About
Just a list of resources and comments regarding algorithms and algorithm techniques.

## Amortized Analysis

There are three common methods to perform amortized analysis (1) aggregate analysis,(2) accounting method, (3) potential method. The main difference is the way the cost is assigned.    

**Amortized Bounds**   
- Assign costs for each operations (an amortized cost), such that you "preserve the sum"
The Amortized Cost of the Sum(of-operations)  >= The Actual Costs of the Sum(of-operations)    

**E.g.**
2-3 trees achieve:
- *O(1)* worst-case per create-empty
- *O(log n^\*)* amortized per insert
- *0* time (zero-time) per delete, in an amortized sense (deletion you can think of as a free operation)

\* Indicates that not every operation always has the same cost. When you start with an empty structure insertion costs is constant O(1).

### Aggregate Analysis
The gist is that we want to fairly assess the overall time complexity of a data structures, and we want to understand how a given data structure actually performs in practice. **We do this by looking the time complexity of performing a sequence of operations over time and averaging it out**.     

**STEPS:**   
1. Show that a sequence of *n* operations takes *T(n)* time in the worst case
2. Show that each operation takes *T(n) / n* on average - the amortized cost (average cost) per operation is *T(n) / n*   

**NOTE:**   
1. Gives average performance of each operation in the worst case
2. This method is less precise than other methods, as all operations are assigned *the same cost*
3. Aggregate method is the weakest method, but most intuitive

#### References 
- [MIT OCW - Amortization: Amortized Analysis](https://www.youtube.com/watch?v=3MpzavN3Mco)
- [Brilliant: Amortized Analysis](https://brilliant.org/wiki/amortized-analysis/)

## Parallel Algorithms
In parallel algorithm we use the concepts like a shared-memory abstract machine called [PRAM: Parallel random-access machine](https://en.wikipedia.org/wiki/Parallel_random-access_machine).    

### Performance Evaluation
 - **Parallel running time** is measured in same manner as with sequential computers
 - **Work** (usually called **Cost**) is the product  of the parallel running time and number of PEs
 - **Work** often has another meaning, namely the sum of the actual running time for each PE
 - **Work Efficient** (usually **Cost Optimal**): A parallel algorithm for which the work/cost is in the same complexity class as an optimal sequential algorithm
 - For simplification, we treat ```work``` and ```cost``` equivalent
 - Parllel runtime is when an entire single process will end    
 - ```Work Cost = Parallel runtime * PR(processor elements)```

**NOTE:**
In distributed algorithms the structure is not there, where as parallel there is a standard type of network.   
In distributed algorithms, there's a third dimension which is communication cost.

### Memory Access Types
In PRAM there two memory access types: (1) **Concurrent** or (2) **Exclusive**
- EREW: Exclusive Read Exclusive Write - one of the most popular
- CREW: Concurrent Read Exclusive Write - also very popular
- ERCW: Exclusive Read Concurrent Write - not often used
- CRCW: Concurrent Read Concurrent Write - most powerful, also very popular

### Example: List Ranking

#### References
- [Chapter 30: Algorithms For Parallel Computers](http://staff.ustc.edu.cn/~csli/graduate/algorithms/book6/chap30.htm)
- [List Ranking and List Scan](http://www.cs.cmu.edu/~scandal/alg/listrank.html)
- [Parallel Algorithms](http://www.cs.cmu.edu/afs/cs/academic/class/15750-s11/www/handouts/par-notes.pdf)
- [Parallel and Distributed Algorithms](https://cse.iitkgp.ac.in/~debdeep/courses_iitkgp/PAlgo/Autumn16-17/slides/Lect7Color.pdf)
