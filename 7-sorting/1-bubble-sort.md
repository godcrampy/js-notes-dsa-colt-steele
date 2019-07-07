# Bubble Sort
Uses two for loop. In every pass, the largest value of the unsorted array is added to  the sorted array.

## Complexity
1. Time

* Normal Version
	* All: O(n<sup>2</sup>)

* Optimized Version
	* Best: O(n)
	* Avg: O(n<sup>2</sup>)
	* Worst: O(n<sup>2</sup>)


2. Space
* All: O(1)

## Implemantation
```javascript
function bubbleSort(array) {
    for (let i = 0; i < array.length; i++)
        for (j = array.length - 1; j > i; j--)
            if (array[j] < array[j - 1])
                [array[j], array[j - 1]] = [array[j - 1], array[j]];
            // ES6 Swap ^
}
```

```javascript
// Optimized
function bubbleSort(array) {
    let didDoSwapping = false;
    for (let i = 0; i < array.length; i++) {
        didDoSwapping = false;
        for (j = array.length - 1; j > i; j--) {
            if (array[j] < array[j - 1]) {
                [array[j], array[j - 1]] = [array[j - 1], array[j]];
                didDoSwapping = true;
            }
        }
        if (!didDoSwapping)
            break;
    }
}
```