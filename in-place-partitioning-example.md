# Example of in-place partitioning

## Overview 

Initial array:

```python
[6, 4, 3, 1, 8, 7, 9, 2, 10, 5]
```

We choose the first value as the pivot: `array[0]` = 6.

Summary of steps:

```python
[6, 4, 3, 1, 8, 7, 9, 2, 10, 5] # no change
[6, 4, 3, 1, 8, 7, 9, 2, 10, 5] # no change
[6, 4, 3, 1, 8, 7, 9, 2, 10, 5] # no change
[6, 4, 3, 1, 8, 7, 9, 2, 10, 5] # no change
[6, 4, 3, 1, 8, 7, 9, 2, 10, 5] # no change
[6, 4, 3, 1, 8, 7, 9, 2, 10, 5] # no change
[6, 4, 3, 1, 2, 7, 9, 8, 10, 5] # swap 2 and 8
[6, 4, 3, 1, 2, 7, 9, 8, 10, 5] # no change
[6, 4, 3, 1, 2, 5, 9, 8, 10, 7] # swap 5 and 7
[5, 4, 3, 1, 2, 6, 9, 8, 10, 7] # swap 6 and 5
```

Final partitioned array:
```
[5, 4, 3, 1, 2, 6, 9, 8, 10, 7]
```

## Description of each step

Let's now go through our example in a more verbose way.

We choose the first element as the pivot, its value is 6. 
Our "smaller" subset has a length of zero and the first element after it is at `index` = 1. Let's now traverse the array:

* `array[1]` = 4, it is smaller than the pivot, we swap it with element at `array[index]` i.e. itself and increment index
* `array[2]` = 3, it is smaller than the pivot, we swap it with element at `array[index]` i.e. itself and increment index
* `array[3]` = 1, it is smaller than the pivot, we swap it with element at `array[index]` i.e. itself and increment index

Note: so far nothing has changed. We have been through 3 values smaller than the pivot so we have simply increased the index marking the end of the "smaller" subset.

* `array[4]` = 8, it is bigger than the pivot, we do nothing
* `array[5]` = 7, it is bigger than the pivot, we do nothing
* `array[6]` = 9, it is bigger than the pivot, we do nothing

Note: we still haven't swapped anything, we have just skipped three bigger values but our `index` remained at 4.

* `array[7]` = 2, it is smaller than the pivot, we swap it with element at `array[index]` (i.e. 8) and increment index
* `array[8]` = 10, it is bigger than the pivot, we do nothing
* `array[9]` = 5, it is smaller than the pivot, we swap it with element at `array[index]` (i.e. 7) and increment index

We now have reached the end of the array. The last element belonging to the smaller subset is located at `index - 1` = 5. We swap it with our pivot, and voilà!
