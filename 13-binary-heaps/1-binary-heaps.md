# Binary Heap
Binary Heaps are Binary Trees with some rules. Binary Heaps are as compact as possible
* **Min Binary Heap**: The parent nodes are always smaller than the child nodes
* **MAx Binary Heap**: The parent nodes are always greater than the child nodes

## Representation
Since heaps are as compact as possible, we can expresss them as an array:
```
				    8
				   / \
				  7   3
				 / \ /
				5  6 2  
				|=> [8, 7, 3, 5, 6, 2]
```
Thus the child nodes and parent nodes are related by index as follows:
1. If parent is at index n:
* left child is at index 2n + 1
* right child is at index 2n + 2

2. If child is at index n, parent is at Math.floor((n-1)/2)

## Implementation
1. **Insert**: Used to insert a value to the heap. First the value is added to the array using ```push```. Then as long as the parent node is smaller then the current node, they are swapped with each other.
2. **Remove**: Used to remove a node from the heap. The node to be removed is swapped with the last node on the array and then removed using ```pop```. Then since a smaller element has risen to the top, this node is trickled down by swapping it with the larger child as long as either of the child has larger value than this node.
```javascript
class MaxBinaryHeap {
    constructor() {
        this.values = []
    }
    parentIndex(index) {
        if (index === 0) return 0;
        return Math.floor((index - 1) / 2)
    }
    parentValue(index) {
        return this.values[this.parentIndex(index)];
    }
    childIndexLeft(index) {
        let final = 2 * index + 1;
        if (final >= this.values.length) return index
        return final;
    }
    childIndexRight(index) {
        let final = 2 * index + 2;
        if (final >= this.values.length) return index
        return final;
    }
    childValueLeft(index) {
        return this.values[this.childIndexLeft(index)];
    }
    childValueRigth(index) {
        return this.values[this.childIndexRight(index)];
    }
    insert(value) {
        this.values.push(value)
        let currentIndex = this.values.length - 1;
        while (this.parentValue(currentIndex) < this.values[currentIndex]) {
            [this.values[currentIndex], this.values[this.parentIndex(currentIndex)]] = [this.values[this.parentIndex(currentIndex)], this.values[currentIndex]]
            currentIndex = this.parentIndex(currentIndex);
        }
    }
    remove(value) {
        let currentIndex = this.values.indexOf(value);
        // swap with the last
        [this.values[currentIndex], this.values[this.values.length - 1]] = [this.values[this.values.length - 1], this.values[currentIndex]];
        this.values.pop();
        while (this.values[currentIndex] < this.childValueLeft(currentIndex) || this.values[currentIndex] < this.childValueRigth(currentIndex)) {
            if (this.childValueLeft(currentIndex) > this.childValueRigth(currentIndex)) {
                //swap with left
                [this.values[currentIndex], this.values[this.childIndexLeft(currentIndex)]] = [this.values[this.childIndexLeft(currentIndex)], this.values[currentIndex]];
                currentIndex = this.childIndexLeft(currentIndex);
            } else {
                // swap with right guy
                [this.values[currentIndex], this.values[this.childIndexRight(currentIndex)]] = [this.values[this.childIndexRight(currentIndex)], this.values[currentIndex]];
                currentIndex = this.childIndexRight(currentIndex);
            }
        }
    }
}
```

## Complexity
1. Insertion: log(n)
1. Removal: log(n)

## Priority Queues
Priority Queues are datastructures in which the elements with higher priority are sered first. These are used by the Operating System to execute important tasks first. Prioritty Wueues are implemented using heaps since the root node is always the larget value. Thus the taks are queued in a heap and when the root task is performed, it is removed as in above implementation and the next higher values comes to the top and so on. If instead arrays were used, we would take O(n) time to find the max which is slower.

> Project Ideas: Implement a todo list app using priority queue