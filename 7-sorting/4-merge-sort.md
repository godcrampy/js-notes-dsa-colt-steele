# Merge Sort
Works on divide and conquer algorithm. General strategy is to keep on splitting the arrays into halves then merging the halves one by one.

## Complexity
1. Time
* All: O(nlog(n))
> Suppose some set of data takes time t. Now if we double the data, we have to make one more splitting step. This is log(n) pattern. But for this additional step we have to make n comparisions as well in the merging step. Thus we get O(nlog(n))

2. Space
* All : O(n)
> More double length of left and right arrays created as n doubles

> Coding Pattern: Avoid while true with breaks inside as it makes the code harder to understand.

### Implementation
```javascript
function mergeSort(array) {
    if (array.length <= 1) return array;
    let midpoint = Math.floor(array.length / 2)
    let left = mergeSort(array.slice(0, midpoint));
    let right = mergeSort(array.slice(midpoint));
    return mergeArrays(left, right);
}

function mergeArrays(array1, array2) {
    // Given two functions, this function constructs a single sorted array
    let sortedArray = [],
        pointer1 = 0,
        pointer2 = 0;
    while (pointer1 != array1.length && pointer2 != array2.length)
        if (array1[pointer1] > array2[pointer2]) {
            sortedArray.push(array2[pointer2]);
            pointer2++;
        } else {
            sortedArray.push(array1[pointer1]);
            pointer1++;
        }
    if (pointer1 == array1.length)
        sortedArray = sortedArray.concat(array2.slice(pointer2));
    else
        sortedArray = sortedArray.concat(array1.slice(pointer1));
    return sortedArray
}
```