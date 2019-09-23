<h3 align="center"> Irvin's Awesome Review / List of Algorithm Resources</h3>
<p align="center"> ༼ つ ◕_◕ ༽つ</p>

## Contents

- [About](#about)
- [Amortized Analysis](#amortized-analysis)

## About
Just a list of resources and comments regarding algorithms and algorithm techniques.

## Amortized Analysis

There are three common methods to perform amortized analysis (1) aggregate analysis,(2) accounting method, (3) potential method. The main difference is the way the cost is assigned.

### Aggregate Analysis
The gist is that we want to fairly assess the overall time complexity of a data structures, and we want to understand how a given data structure actually performs in practice. **We do this by looking the time complexity of performing a sequence of operations over time and averaging it out**.     

**STEPS:**   
1. Show that a sequence of *n* operations takes *T(n)* time in the worst case
2. Show that each operation takes *T(n) / n* on average - the amortized cost (average cost) per operation is *T(n) / n*   

**NOTE:**   
1. Gives average performance of each operation in the worst case
2. This method is less precise than other methods, as all operations are assigned *the same cost*
3. Aggregate method is the weakest method, but most intuitive
