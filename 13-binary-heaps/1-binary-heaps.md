# Binary Heap
Binary Heaps are Binary Trees with some rules. Binary Heaps are as compact as possible
* **Min Binary Heap**: The parent nodes are always smaller than the child nodes
* **MAx Binary Heap**: The parent nodes are always greater than the child nodes

## Representation
Since heaps are as compact as possible, we can compress them in an array:
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