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
