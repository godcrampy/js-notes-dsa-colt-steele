# Quick Sort
Sorts elements one by one by placing a pivot element in its correct place and then repeating for the left and right elements recursively.

## Complexity
1. Time

* Best, Avg: O(nlog(n))
* Worst: O(n<sup>2</sup>) 

> If certain data takes time t and we double the data, we need to make one morebreaking od array into left and right and for that one extra array we need to compare n times. Thus O(nlog(n)). Worst case comes when the array is already sorted. The pivot will be at its position and we will make n comparisions to move to the next postion which will be at its postion as well and so on for n times. Thus we get O(n<sup>2</sup>). I way to avoid this is by using ```isSorted(array)``` which checks if an array is sorted.

2. Space

* All: O(log(n))

> When array size is doubled, call stack increases by one (Not satisfied with the answer coz this reasoning fails at merge sort)

## Implementation
```javascript
function quickSort(array) {
    if (array.length <= 1) return array;
    let pivot = array[0];
    let pivotPosition = 0;
    for (let i = 1; i < array.length; i++)
        if (array[i] < pivot) {
            pivotPosition++;
            [array[pivotPosition], array[i]] = [array[i], array[pivotPosition]];
        }
    [array[0], array[pivotPosition]] = [array[pivotPosition], array[0]];
    let left = quickSort(array.slice(0, pivotPosition));
    let right = quickSort(array.slice(pivotPosition + 1));
    return [...left, pivot, ...right];
}
```