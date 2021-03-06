# Sorting Algorithms

## Table of Contents
- [Bubble Sort](#bubble-sort)
- [Selection Sort](#selection-sort)
- [Insertion Sort](#insertion-sort)
- [Merge Process](#merge-process)
- [2-way Merge Sort](#2-way-merge-sort)
- [Merge Sort](#merge-sort)
- [Quick Sort](#quick-sort)
- [Bucket Sort](#bucket-sort)
- [Radix Sort](#radix-sort)

## Bubble Sort
Instead of searching the entire array, bubble sort works by comparing **adjacent pairs** of objects in the array.   
If the objects are not in the correct order, they are **swapped** so that the largest of the two moves up.   
This process continues until the largest of the objects, eventually "bubbles" up to the highest position in the array.   
After this occurs, the search for the next largest object begins.   
The swapping continues until the whole array is in the correct order.   


### Pseudocode
```
Set swap counter to a non-zero value
Repeat until the swap counter is 0:
  Reset swap counter to 0
  Look at each adjacent pair
    If two adjacent elements are not in order, swap them and add one to the swap counter
```

### Example Code

```cpp
void bubbleSort(int ar[])
{
  for (int i = (ar.length - 1); i >= 0; i--)
  {
    for (int j = 1; j ≤ i; j++)
    {
      if (ar[j-1] > ar[j])
      {
        int temp = ar[j-1];
        ar[j-1] = ar[j];
        ar[j] = temp;
      }
    }
  } 
}
```

### Example

We take an unsorted array.
|index|  1 |  2 | 3  | 4  |  5 |
|-----| ---|:--:| --:|----|----|
|Arr  | 14 | 33 | 27 | 35 | 10 |

Compare the very first two elements, check which one is greater.   
|index| :grey_question:| :grey_question:| 3  | 4  |  5 |
|-----| ---------|:--------:| --:|----|----|
|Arr  | **14** | **33** | 27 | 35 | 10 |

In this case, value ***33*** is greater than ***14***, so both elements are in the right sorted location.   
Next, we compare ***33*** with ***27***.
|index|  1 | :grey_question:| :grey_question:| 4  |  5 |
|-----|----|:--------:| --------:|----|----|
|Arr  | 14 | **33** | **27** | 35 | 10 |

We see that ***27*** is smaller than ***33***. We swap these two values.
|index|  1 | :point_right: | :point_left:| 4  |  5 |
|-----|----|:--------:| --------:|----|----|
|Arr  | 14 | ***33*** | ***27*** | 35 | 10 |

The new array looks as follows:
|index|  1 | 2  | 3  | 4  |  5 |
|-----|----|---:|----|----|----|
|Arr  | 14 | 27 | 33 | 35 | 10 |

Next we compare ***33*** and ***35***.   
Both elements are already in sorted positions.   
|index|  1 | 2  |:grey_question:|:grey_question:|  5 |
|-----|----|---:|--------|--------|----|
|Arr  | 14 | 27 | **33** | **35** | 10 |

We move to the next two values, ***35*** and ***10***.
|index|  1 | 2  | 3  |:grey_question:|:grey_question:|
|-----|----|---:|----|--------|--------|
|Arr  | 14 | 27 | 33 | **35** | **10** |

We see that ***10*** is smaller than ***35***.   
They are not in sorted order.   
|index|  1 | 2  | 3  | :point_right: | :point_left: |
|-----|----|---:|----|----------|----------|
|Arr  | 14 | 27 | 33 | ***35*** | ***10*** |

We swap these two elements.   
We find that we have reached the end of the arrays - we have completed one iteration.    
We have bubbled the largest element (**35**) to the end of the array.    
The array should look as follows:


|index|  1 | 2  | 3  | 4  | :heavy_check_mark: |
|-----|----|---:|----|----|----|
|Arr  | 14 | 27 | 33 | 10 | 35 |

**Iteration 1 Completed.**   

We move on to the **second iteration**.   


|index| :grey_question: | :grey_question: | 3  | 4  | :heavy_check_mark: |
|-----|----|---:|----|----|----|
|Arr  | **14** | **27** | 33 | 10 | 35 |


|index| 1 | :grey_question: | :grey_question:  | 4 | :heavy_check_mark: |
|-----|----|---:|----|----|----|
|Arr  | 14 | **27** | **33** | 10 | 35 |


|index| 1 | 2 | :grey_question:  | :grey_question: | :heavy_check_mark: |
|-----|----|---:|----|----|----|
|Arr  | 14 | 27 | **33** | **10** | 35 |


|index| 1 | 2 | :point_right: | :point_left: | :heavy_check_mark: |
|-----|----|---:|----|----|----|
|Arr  | 14 | 27 | ***33*** | ***10*** | 35 |


|index| 1 | 2 | 3 | :heavy_check_mark: | :heavy_check_mark:|
|-----|----|---:|----|----|----|
|Arr  | 14 | 27 | 10 | 33 | 35 |

After the **second iteration** the largest element in the unsorted part of the array (**33**) has been **bubbled** the end of the array.

**Iteration 2 Completed.**   

We move on to the **third iteration**.   

|index| :grey_question:| :grey_question:| 3 | :heavy_check_mark: | :heavy_check_mark:|
|-----|----|---:|----|----|----|
|Arr  | **14** | **27** | 10 | 33 | 35 |

|index| 1 | :grey_question: | :grey_question:  | :heavy_check_mark: | :heavy_check_mark:|
|-----|----|---:|----|----|----|
|Arr  | 14 | **27** | **10** | 33 | 35 |

|index| 1 | :point_right: | :point_left: | :heavy_check_mark: | :heavy_check_mark:|
|-----|----|---:|----|----|----|
|Arr  | 14 | **27** | **10** | 33 | 35 |

|index| 1 | 2 | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark:|
|-----|----|---:|----|----|----|
|Arr  | 14 | 10 | 27 | 33 | 35 |

After the **third iteration** the largest element in the unsorted part of the array (**27**) has been **bubbled** the end of the array.

**Iteration 3 Completed.**   

We move on to the **fourth iteration**.   

|index| :grey_question: | :grey_question: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark:|
|-----|----|---:|----|----|----|
|Arr  | **14** | **10** | 27 | 33 | 35 |

|index| :point_right: | :point_left: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark:|
|-----|----|---:|----|----|----|
|Arr  | ***14*** | ***10*** | 27 | 33 | 35 |

|index| 1 | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark:|
|-----|----|---:|----|----|----|
|Arr  | 10 | 14 | 27 | 33 | 35 |

After the **fourth iteration** the largest element in the unsorted part of the array (**14**) has been **bubbled** down.

**Iteration 4 Completed.**   

We move on to the **fifth iteration**.   
No more swaps are required. Bubble sort learns that the array is completely sorted.

|index| :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark:|
|-----|----|---:|----|----|----|
|Arr  | 10 | 14 | 27 | 33 | 35 |

### Analysis
The average and worst case complexity of Bubble Sort is ***O(n^2)*** where ***n*** is the number of items in the list.   

### References
- [TutorialsPoint - Bubble Sort](https://www.tutorialspoint.com/data_structures_algorithms/bubble_sort_algorithm.htm)
- [Business Data Structures](http://www.pkirs.utep.edu/CIS3355/Tutorials/chapter9/tutorial9A/bubblesort.htm)

## Selection Sort
It's an **in-place** comparison-based algorithm, where the list is divided into two parts, the sorted part at the left end and the unsorted part at the right end. Initially, the sorted part is empty and the entire unsorted part is the entire list.   

The smallest element is selected from the unsorted part of the array and it is swapped with the left most element in the unsorted part; that element becomes part of the sorted array. This process continues moving the unsorted array boundary by one element to the right.


### Pseudocode
```
Repeat until no unsorted elements remain:
  Search the unsorted part of the data to find the smallest values
  Swap the smallest found value with the first element of the unsorted part
```

More explicit pseudocode:
```
Step 1 − Set MIN to location 0
Step 2 − Search the minimum element in the list
Step 3 − Swap with value at location MIN
Step 4 − Increment MIN to point to next element
Step 5 − Repeat until list is sorted
```
### Example Code

```cpp
void selectionSort(int[] ar) 
{
  for (int i = 0; i ‹ ar.length-1; i++)
  {
    int min = i;
    for (int j = i+1; j ‹ ar.length; j++)
      if (ar[j] ‹ ar[min]) min = j;
    int temp = ar[i];
    ar[i] = ar[min];
    ar[min] = temp;
  }
}
```

### Example

Consider the following array:
|index| 1  | 2  | 3  | 4  | 5  | 6  | 7  | 8  |
|-----|----|---:|----|----|----|----|----|----|
|Arr  | 14 | 33 | 27 | 10 | 35 | 19 | 42 | 44 |

We begin at index 1 with value **14**, and scan the entire list for the smallest value.   
Value **10** is the lowest value in the unsorted part of the array (the entire array for now).
|index| :round_pushpin: | 2  | 3  |:+1:| 5  | 6  | 7  | 8  |
|-----|----|---:|----|----|----|----|----|----|
|Arr  | 14 | 33 | 27 | 10 | 35 | 19 | 42 | 44 |

These two values are swapped.
|index| :point_right: | 2  | 3  | :point_left:  | 5  | 6  | 7  | 8  |
|-----|----|---:|----|----|----|----|----|----|
|Arr  | 14 | 33 | 27 | 10 | 35 | 19 | 42 | 44 |

After one iteration 10, which happens to be the minimum value in the list, appears in the first position of the sorted list.   

|index| :heavy_check_mark: | 2  | 3  | 4 | 5  | 6  | 7  | 8  |
|-----|----|---:|----|----|----|----|----|----|
|Arr  | 10 | 33 | 27 | 14 | 35 | 19 | 42 | 44 |

We move our marker to the second position of the array. 
This indicates the start of the unsorted part of the list.
Then, we once again scan the list in a linear manner - searching for the smallest element.
|index| :heavy_check_mark: | :round_pushpin:  | 3  | 4 | 5  | 6  | 7  | 8  |
|-----|----|---:|----|----|----|----|----|----|
|Arr  | 10 | 33 | 27 | 14 | 35 | 19 | 42 | 44 |

Value **14** is found to be the smallest value in the unsorted part of the list.
|index| :heavy_check_mark: | :round_pushpin:  | 3  | :+1: | 5  | 6  | 7  | 8  |
|-----|----|---:|----|----|----|----|----|----|
|Arr  | 10 | 33 | 27 | 14 | 35 | 19 | 42 | 44 |

We swap it with the far left element in the unsorted part of the list.
|index| :heavy_check_mark: | :point_right:  | 3  | :point_left: | 5  | 6  | 7  | 8  |
|-----|----|---:|----|----|----|----|----|----|
|Arr  | 10 | 33 | 27 | 14 | 35 | 19 | 42 | 44 |


**14** is now part of the sorted part of the list.
|index| :heavy_check_mark: | :heavy_check_mark:  | 3  | 4 | 5  | 6  | 7  | 8  |
|-----|----|---:|----|----|----|----|----|----|
|Arr  | 10 | 14 | 27 | 33 | 35 | 19 | 42 | 44 |

**Third Iteration**

|index| :heavy_check_mark: | :heavy_check_mark:  | :round_pushpin:  | 4 | 5  | 6  | 7  | 8  |
|-----|----|---:|----|----|----|----|----|----|
|Arr  | 10 | 14 | 27 | 33 | 35 | 19 | 42 | 44 |

|index| :heavy_check_mark: | :heavy_check_mark:  | :round_pushpin:  | 4 | 5  | :+1:  | 7  | 8  |
|-----|----|---:|----|----|----|----|----|----|
|Arr  | 10 | 14 | 27 | 33 | 35 | 19 | 42 | 44 |

|index| :heavy_check_mark: | :heavy_check_mark:  | :point_right:  | 4 | 5  | :point_left:  | 7  | 8  |
|-----|----|---:|----|----|----|----|----|----|
|Arr  | 10 | 14 | 27 | 33 | 35 | 19 | 42 | 44 |

|index| :heavy_check_mark: | :heavy_check_mark:  | :heavy_check_mark:  | 4 | 5  | 6 | 7  | 8  |
|-----|----|---:|----|----|----|----|----|----|
|Arr  | 10 | 14 | 19 | 33 | 35 | 27 | 42 | 44 |

**Fourth Iteration**

|index| :heavy_check_mark: | :heavy_check_mark:  | :heavy_check_mark:  | :round_pushpin: | 5  | 6 | 7  | 8  |
|-----|----|---:|----|----|----|----|----|----|
|Arr  | 10 | 14 | 19 | 33 | 35 | 27 | 42 | 44 |

|index| :heavy_check_mark: | :heavy_check_mark:  | :heavy_check_mark:  | :round_pushpin: | 5  | :+1: | 7  | 8  |
|-----|----|---:|----|----|----|----|----|----|
|Arr  | 10 | 14 | 19 | 33 | 35 | 27 | 42 | 44 |

|index| :heavy_check_mark: | :heavy_check_mark:  | :heavy_check_mark:  | :point_right: | 5  | :point_left: | 7  | 8  |
|-----|----|---:|----|----|----|----|----|----|
|Arr  | 10 | 14 | 19 | 33 | 35 | 27 | 42 | 44 |

|index| :heavy_check_mark: | :heavy_check_mark:  | :heavy_check_mark:  | :heavy_check_mark: | 5  | 6 | 7  | 8  |
|-----|----|---:|----|----|----|----|----|----|
|Arr  | 10 | 14 | 19 | 27 | 35 | 33 | 42 | 44 |

**Fifth Iteration**

|index| :heavy_check_mark: | :heavy_check_mark:  | :heavy_check_mark:  | :heavy_check_mark: | :round_pushpin: | 6 | 7  | 8  |
|-----|----|---:|----|----|----|----|----|----|
|Arr  | 10 | 14 | 19 | 27 | 35 | 33 | 42 | 44 |

|index| :heavy_check_mark: | :heavy_check_mark:  | :heavy_check_mark:  | :heavy_check_mark: | :round_pushpin: | :+1: | 7  | 8  |
|-----|----|---:|----|----|----|----|----|----|
|Arr  | 10 | 14 | 19 | 27 | 35 | 33 | 42 | 44 |

|index| :heavy_check_mark: | :heavy_check_mark:  | :heavy_check_mark:  | :heavy_check_mark: | :point_right: | :point_left: | 7  | 8  |
|-----|----|---:|----|----|----|----|----|----|
|Arr  | 10 | 14 | 19 | 27 | 35 | 33 | 42 | 44 |

|index| :heavy_check_mark: | :heavy_check_mark:  | :heavy_check_mark:  | :heavy_check_mark: | :heavy_check_mark: | 6 | 7  | 8  |
|-----|----|---:|----|----|----|----|----|----|
|Arr  | 10 | 14 | 19 | 27 | 33 | 35 | 42 | 44 |

**Sixth Iteration**

|index| :heavy_check_mark: | :heavy_check_mark:  | :heavy_check_mark:  | :heavy_check_mark: | :heavy_check_mark: | :round_pushpin: | 7  | 8  |
|-----|----|---:|----|----|----|----|----|----|
|Arr  | 10 | 14 | 19 | 27 | 33 | 35 | 42 | 44 |


|index| :heavy_check_mark: | :heavy_check_mark:  | :heavy_check_mark:  | :heavy_check_mark: | :heavy_check_mark: | :round_pushpin: :+1: | 7  | 8  |
|-----|----|---:|----|----|----|----|----|----|
|Arr  | 10 | 14 | 19 | 27 | 33 | 35 | 42 | 44 |

We do nothing, **35** is already in the sorted location

|index| :heavy_check_mark: | :heavy_check_mark:  | :heavy_check_mark:  | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | 7  | 8  |
|-----|----|---:|----|----|----|----|----|----|
|Arr  | 10 | 14 | 19 | 27 | 33 | 35 | 42 | 44 |

**Seventh Iteration**

|index| :heavy_check_mark: | :heavy_check_mark:  | :heavy_check_mark:  | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :round_pushpin: | 8  |
|-----|----|---:|----|----|----|----|----|----|
|Arr  | 10 | 14 | 19 | 27 | 33 | 35 | 42 | 44 |

|index| :heavy_check_mark: | :heavy_check_mark:  | :heavy_check_mark:  | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :round_pushpin: :+1: | 8  |
|-----|----|---:|----|----|----|----|----|----|
|Arr  | 10 | 14 | 19 | 27 | 33 | 35 | 42 | 44 |

We do nothing, **42** is in the right sorted location.
|index| :heavy_check_mark: | :heavy_check_mark:  | :heavy_check_mark:  | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | 8  |
|-----|----|---:|----|----|----|----|----|----|
|Arr  | 10 | 14 | 19 | 27 | 33 | 35 | 42 | 44 |

**Eight Iteration**
|index| :heavy_check_mark: | :heavy_check_mark:  | :heavy_check_mark:  | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :round_pushpin:  |
|-----|----|---:|----|----|----|----|----|----|
|Arr  | 10 | 14 | 19 | 27 | 33 | 35 | 42 | 44 |

We are on the last element.
|index| :heavy_check_mark: | :heavy_check_mark:  | :heavy_check_mark:  | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :round_pushpin: :+1: |
|-----|----|---:|----|----|----|----|----|----|
|Arr  | 10 | 14 | 19 | 27 | 33 | 35 | 42 | 44 |

We do nothing, **44** is already in the sorted location.
|index| :heavy_check_mark: | :heavy_check_mark:  | :heavy_check_mark:  | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
|-----|----|---:|----|----|----|----|----|----|
|Arr  | 10 | 14 | 19 | 27 | 33 | 35 | 42 | 44 |

### References
- [TutorialsPoint - Selection Sort](https://www.tutorialspoint.com/data_structures_algorithms/selection_sort_algorithm.htm)

## Insertion Sort

### References

- [TutorialsPoint - Insertion Sort](https://www.tutorialspoint.com/data_structures_algorithms/insertion_sort_algorithm.htm)
- [CMU Adamchik - Sorting](https://www.cs.cmu.edu/~adamchik/15-121/lectures/Sorting%20Algorithms/sorting.html)

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

## Quick Sort

### Overview

We take a random number on the list, called a **pivot**, so that all the smaller things are on the left and all the larger things are on the right.   

So, how do we choose the pivot point?   
- Various ways to choose the pivot point
- The last element is the most common way



### Analysis
The worst case for QuickSort occurs when the pivot is the unique minimum or maximum element.   
In this case either the left or right subarray will have a size of ***n - 1*** and the other has 0.   
The running time is proportional to the sum ***n + (n - 1) + ... + 2 + 1***.   
Thus, the worst case running time of QuickSort is ***O(n^2)***.

**Average case:** O(nlogn)

**Worst case:** O(n^2)

But, **note** that unlike Merge Sort, Quick Sort is **in-place**. It does not require additional space.   
This is unlike Merge Sort which has an **O(n)** space complexity.   

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

### Quick Sort Algorithm

```cpp
QuickSort( low, high ) {
  if( low < high ) {
    j = Partition( low, high )
    QuickSort( low, j )
    QuickSort( j + 1, high )
  }
}
```

### Example

|index| 0 | 1  | 2  | 3  | 4  | 5  | 6  | 7  |
|-----|---|----|---:|----|----|----|----|----|
|Arr  | 7 | 2  | 1  | 6  | 8  | 5  | 3  | 4  |

Select Pivot

|index| 0 | 1  | 2  | 3  | 4  | 5  | 6  | :arrow_down_small: |
|-----|---|----|---:|----|----|----|----|----|
|Arr  | 7 | 2  | 1  | 6  | 8  | 5  | 3  | 4  |


|index| 0 | 1  | 2  | :arrow_down_small: | 4  | 5  | 6  | 7 |
|-----|---|----|---:|----|----|----|----|----|
|Arr  | 2 | 1  | 3  | 4  | 8  | 5  | 7  | 6  |


|index| 0 | 1  | 2  |    | 4  | 5  | 6  | 7  |
|-----|---|----|---:|----|----|----|----|----|
|Arr  | 2 | 1  | 3  |    | 8  | 5  | 7  | 6  |


Let's further explore the far left side of the partition.
|index| 0 | 1  | :arrow_down_small: |    | 4  | 5  | 6  | 7 |
|-----|---|----|---:|----|----|----|----|----|
|Arr  | 2 | 1  | 3  |    | 8  | 5  | 7  | 6  |


Since there's only values smaller than **3** then all the values go to the left.
|index| 0 | 1  |   |   |   |   |   |   |
|-----|---|----|---|---|---|---|---|---|
|Arr  | 2 | 1  |   | X |   |   |   |   |

|index| 0 | :arrow_down_small:  |   |   |   |   |   |   | 
|-----|---|----|---|---|---|---|---|---|
|Arr  | 2 | 1  |   |   |   |   |   |   |

|index| 0 | 1  |   |   |   |   |   |   |
|-----|---|----|---|---|---|---|---|---|
|Arr  | 1 | 2  |   |   |   |   |   |   |

|index|   | 1  |   |   |   |   |   |   |
|-----|---|----|---|---|---|---|---|---|
|Arr  |   | 2  |   |   |   |   |   |   |


Indices 0 - 3 have been sorted.
|index| 0 | 1 | 2 | 3 |   |   |   |   |
|-----|---|---|---|---|---|---|---|---|
|Arr  | 1 | 2 | 3 | 4 |   |   |   |   |

Now we can work on the segement from index 4 - 7.




### References
- [Quick Sort Algorithm by MyCodeSchool](https://www.youtube.com/watch?v=COk73cpQbFQ)
- [Quick Sort Algorithm Analysis by MyCodeSchool](https://www.youtube.com/watch?v=3Bbm3Prd5Fo)
- [Quick Sort Algorithm by Abdul Bari](https://www.youtube.com/watch?v=7h1s2SojIRw)
- [Quick Sort by RobEdwardsSDSU](https://www.youtube.com/watch?v=ZHVk2blR45Q)

## Bucket Sort
Bucket sort is abount creating buckets and distributing data across these buckets.   
Each bucket can hold a similar type of data.   
Afer distributing, each bucket is sorted using another sorting algorithm.   
After that, all elements are gathered on the main list to get the sorted form.   

### Pseudocode
``` javascript
bucketSort()
  create N buckets each of which can hold a range of values
  for all the buckets
    initialize each bucket with 0 values
  for all the buckets
    put elements into buckets matching the range
  for all the buckets 
    sort elements in each bucket
  gather elements from each bucket
end bucketSort
```

### Analysis

**Worst Case Complexity:** ***O(n^2)***
When there are elements of close range in the array, they are likely to be placed in the same bucket. This may result in some buckets having more number of elements than others.   

It makes the complexity depend on the sorting algorithm used to sort the elements of the bucket.   

The copmlexity becomes even worse when the elements are in reverse order. If insertion sort is used to sort elements of the bucket, then the time complexity becomes **O(n^2)**.   

**Best Case Complexity:** ***O(n + k)***
It occurs when the elements are uniformly distributed in the buckets with a nearly equal number of elements in each bucket.   

The complexity becomes even better if the elements inside the buckets are already sorted.   

If insertion sort is used to sort elements of a bucket then the overall complexity in the best case will be linear ie. O(n+k). **O(n)** is the complexity for making the buckets and **O(k)** is the complexity for sorting the elements of the bucket using algorithm having linear time complexity at best case.   

**Average Case Complexity:** ***O(n)***
It occurs when the elements are distributed randomly in the array. Even if the elements are not distributed uniformly, bucket sort runs in linear time. It holds true until the sum of the squares of the bucket sizes is linear in the total number of elements.   

### References
- [Programiz - Bucket Sort](https://www.programiz.com/dsa/bucket-sort)
- [CMU Adamchik - Sorting](https://www.cs.cmu.edu/~adamchik/15-121/lectures/Sorting%20Algorithms/sorting.html)

## Radix Sort

### References
- [Radix Sort - MUST READ](https://medium.com/basecs/getting-to-the-root-of-sorting-with-radix-sort-f8e9240d4224)
