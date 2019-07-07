# Binary Search

Requires sorted array. Unlike linear search which eliminates one number at a time, binary search eliminates half of the array at a time. Works on _divide and conquer._

## Complexity
1. Time
	
	Best: O(1)

	Average: O(log(n))

	Best: O(log(n))

2. Space: O(1)

### Explanation
Suppose we have 16 length array. Is we perform binary search, we half the array overtime repeatedly. So in the worst case 16=>8=>4=>2=>1. Now if we doubled the size of array we will require one extra step. 32=>16=>8=>4=>2=>1. Thus by if complexity is f(n), by doubling n the steps increase by one. Thus f(n) = log(n). Thus O(log(n))

## Implementation
```javascript
//Using recursion
function binarySearch(array, target, left = 0, right = array.length - 1) {
    // find the middle index
    let middle = Math.floor((left + right) / 2)
    if (array[middle] == target) {
        return middle;
    } else if (right == left) {
        return -1;
    } else if (target < array[middle]) {
        // target is in the left array
        return binarySort(array, target, left, middle - 1);
    } else {
        // target is in the right array
        return binarySort(array, target, middle + 1, right);
    }
}

//Using While Loop
function binarySearch(array, target) {
    // Set inital pointers
    let left = 0;
    let right = array.length;
    while (true) {
        let middle = Math.floor((left + right) / 2);
        if (array[middle] === target) return middle;
        if (array.length === 1) return -1;
        if (array[middle] < target) {
            // target belongs to the right;
            left = middle + 1;
        } else {
            // target belongs to the left
            right = middle - 1
        }
    }
}
```