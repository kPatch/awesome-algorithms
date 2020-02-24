# Sorting Algorithms

## Table of Contents
- [Merge Process](#merge-process)
- [2-way Merge Sort](#2-way-merge-sort)
- [Merge Sort](#merge-sort)
- [QuickSort](#quicksort)

## Merge Process
Two sorted list lets combine them.

| List A  | List B  | Merged List C|
| --------|:-------:| ------------:|
|    2    |    5    |              |
|    8    |    9    |              |
|   15    |   12    |              |
|   18    |   17    |              |

Below we denote the merging process, where ***i*** denotes the index in *List A*, and ***j*** denotes the index in *List B*, and ***k*** denotes the index in the *Merged List*.

We start of by comparing *2* and *5* and choosing the smallest value. In this case it's *2*.

| List A       | List B         | Merged List C|
| -------------|:--------------:| ------------:|
|  **i -> 2**  |  **j -> 5**    | **2 <- k**   |
|    8         |    9           |              |
|   15         |   12           |              |
|   18         |   17           |              |

Hence the index in *List A* is increased (*i++*). The index in the *Merged List C* increases as well (*k++*).
| List A       | List B         | Merged List C|
| -------------|:--------------:| ------------:|
|    2         |  **j -> 5**    | 2            |
| **i -> 8**   |    9           |    **<- k**  |
|   15         |   12           |              |
|   18         |   17           |              |

Next, we compare *A[ i ]* with *B[ j ]*.   
The value *8* is greater than *5*, hence we copy *5* into the *Merged List C*.   
The index in *List B* is increased (*j++).   
The index in the *Merged List C* is increased as well (*k++*).   
| List A       | List B         | Merged List C|
| -------------|:--------------:| ------------:|
|    2         |    5           | 2            |
| **i -> 8**   | **j -> 9**     | 5            |
|   15         |   12           |  **<- k**    |
|   18         |   17           |              |

We once again compare *A[ i ]* and *B[ j ]*.   
The value *8* in *List A* is less than *9*, hence we copy *8* into the *Merged List C*.   
The index in *List A* is increased (*i++).    
The index in the *Merged List C* is increased as well (*k++*).   
| List A       | List B         | Merged List C|
| -------------|:--------------:| ------------:|
|    2         |    5           | 2            |
|    8         | **j -> 9**     | 5            |
| **i -> 15**  |   12           | 8            |
|   18         |   17           |  **<- k**    |

We once again compare *A[ i ]* and *B[ j ]*.  
The value *9* in *List B* is less than *15* in *List A*, hence we copy *9* into the *Merged List C*.   
The index in *List B* is increased (*j++).    
The index in the *Merged List C* is increased as well (*k++*).   
| List A       | List B         | Merged List C|
| -------------|:--------------:| ------------:|
|    2         |    5           | 2            |
|    8         |    9           | 5            |
| **i -> 15**  | **j -> 12**    | 8            |
|   18         |   17           | 9            |
|              |                | **<- k**     |


We once again compare *A[ i ]* and *B[ j ]*.  
The value *12* in *List B* is less than *15* in *List A*, hence we copy *12* into the *Merged List C*.   
The index in *List B* is increased (*j++).    
The index in the *Merged List C* is increased as well (*k++*).   
| List A       | List B         | Merged List C|
| -------------|:--------------:| ------------:|
|    2         |    5           | 2            |
|    8         |    9           | 5            |
| **i -> 15**  |   12           | 8            |
|   18         | **j -> 17**    | 9            |
|              |                | 12           |
|              |                | **<- k**     |

We once again compare *A[ i ]* and *B[ j ]*.  
The value *15* in *List A* is less than *17* in *List B*, hence we copy *15* into the *Merged List C*.   
The index in *List A* is increased (*i++).    
The index in the *Merged List C* is increased as well (*k++*).   
| List A       | List B         | Merged List C|
| -------------|:--------------:| ------------:|
|    2         |    5           | 2            |
|    8         |    9           | 5            |
|   15         |   12           | 8            |
| **i -> 18**  | **j -> 17**    | 9            |
|              |                | 12           |
|              |                | 15           |
|              |                | **<- k**     |

We once again compare *A[ i ]* and *B[ j ]*.  
The value *17* in *List B* is less than *18* in *List A*, hence we copy *17* into the *Merged List C*.   
The index in *List B* is increased (*j++).    
The index in the *Merged List C* is increased as well (*k++*).   
| List A       | List B         | Merged List C|
| -------------|:--------------:| ------------:|
|    2         |    5           | 2            |
|    8         |    9           | 5            |
|   15         |   12           | 8            |
| **i -> 18**  |   17           | 9            |
|              |  **j ->**      | 12           |
|              |                | 15           |
|              |                | 17           |
|              |                | **<- k**     |

Lastly, we note that *List B* has gone out of bounds.   
While, *List A* still has remaining values.   
Since the lists are individually sorted, we can just copy over the remaining values of *List A* onto the *Merged List C*.
| List A       | List B         | Merged List C|
| -------------|:--------------:| ------------:|
|    2         |    5           | 2            |
|    8         |    9           | 5            |
|   15         |   12           | 8            |
|   18         |   17           | 9            |
| **i ->**     |  **j ->**      | 12           |
|              |                | 15           |
|              |                | 17           |
|              |                | 18           |

## 2-way Merge Sort
A single list is given, and we have to sort using the merge process.   
We assume each element in the array is a list of a single element.   
Thus, in the following example we have 8 lists.   
| ***index***| 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
|------------|---|---|---|---|---|---|---|---|
|***List A***| 9 | 3 | 7 | 5 | 6 | 4 | 8 | 2 |


|***List A*** (8 lists) |     9    |    3    |    7    |     5     |     6    |    4    |    8    |    2    |
|-----------------------|----------|---------|---------|-----------|----------|---------|---------|---------|
| 1st Pass (4 lists)    | **(** 3, | 9 **)** | **(** 5,|   7 **)** | **(** 4, | 6 **)** | **(** 2,| 8 **)** |
| 2nd Pass (2 lists)    | **(** 3, |    5,   |    7,   |   9 **)** | **(** 2, |    4,   |    6,   | 8 **)** |
| 3rd Pass (1 list)     | **(** 2, |    3,   |    4,   |      5,   |    6,    |    7,   |    8,   | 9 **)** | 

At each pass we divide the list by two. First it's **8 lists**, divided by 2 we get **4 lists**, divided by 2 we get **2 lists**, divided by 2 we get **1 list**.   

The number of passes is **logn**, where **n** represents the number of items in the list.   
But, in each pass there are **n** number of merges. 
So then the total running time is **nLog(n)**, that is ***O(nLogn)***.


Note that when you merge a list you have to use an additional array that will hold the result.

## Merge Sort

**n** elements are merged at each level (at each pass). There are **logn** recursive levels (passes) in total.   
So the total running time is Theta(nLogn).   

### Reference
- [HackerEarth](https://www.hackerearth.com/practice/algorithms/sorting/merge-sort/tutorial/)
- [Runestone Academy](https://runestone.academy/runestone/books/published/pythonds/SortSearch/TheMergeSort.html)

## QuickSort

### Partition

```cpp
Partition( low, high ) {
  pivot = A[low]
  i = low
  j = high
  
  while( i < j ) {
    do {
      i++
    } while( A[i] <= pivot )
    
    do {
      j--
    } while( A[i] <= pivot )
    
    if( i < j ) {
      swap( A[i], A[[j] )
    }
  }
  swap( A[low], A[j] )
  return j;;
}
```

### QuickSort Algorithm

```cpp
QuickSort( low, high ) {
  if( low < high ) {
    j = Partition( low, high )
    QuickSort( low, j )
    QuickSort( j + 1, high )
  }
}
```

### References
- [QuickSort Algorithm by Abdul Bari](https://www.youtube.com/watch?v=7h1s2SojIRw)
- [QuickSort by RobEdwardsSDSU](https://www.youtube.com/watch?v=ZHVk2blR45Q)
