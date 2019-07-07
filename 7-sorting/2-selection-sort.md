# Selection Sort
We go thru the unsorted array and put the smallest value at the beginning and include it in the sorted array. The only place where selection sort is better than bubble is that it has less number of swaps.

## Complexity
1. Time
	* Best: O(n)
	* Avg: O(n<sup>2</sup>)
	* Worst: O(n<sup>2</sup>)


2. Space
	* All: O(1)

## Implementaion
```javascript
function selectionSort(array) {
    let minPosition;
    for (let i = 0; i < array.length - 1; i++) {
        //i represents the position to swap with
        minPosition = i;
        for (let j = i + 1; j < array.length; j++)
            if (array[j] < array[minPosition])
                minPosition = j;
        [array[i], array[minPosition]] = [array[minPosition], array[i]];
    }
}
```