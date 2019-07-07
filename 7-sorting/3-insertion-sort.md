# Insertion Sort
We take one element and insert it in the right place in the sorted part

## Implementation
```javascript
function insertionSort(array) {
    for (let i = 0; i < array.length - 1; i++) {
        // i represents the last element of the sorted half
        let target = array[i + 1];
        for (let j = 0; j <= i; j++) {
            if (array[j] > target) {
                array.splice(j, 0, target);
                array.splice(i + 2, 1);
                break;
            }
        }
    }
}
```