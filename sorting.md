# Sorting Algorithms

## Table of Contents
- [Merge Process](#merge-process)
- [Merge Sort](#merge-sort)

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

## Merge Sort
