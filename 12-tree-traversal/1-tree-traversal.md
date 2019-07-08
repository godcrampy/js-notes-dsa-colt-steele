# Tree Traversal
Traversing a tree means visiting every node on the tree once.

## Types:
1. Breadth First Search
2. Depth First Search
	1. DFS PreOrder
	2. DFS PostOrder
	3. DFS Inorder

##BFS:

To implement BFS, we use queues. We start by adding the root node to the queue. Then as long as the queue is not empty we follow the following algorithm:
1. Dequeue a node
2. Add its value to the list
3. Queue its left and right parameters to the queue

```javascript
// Inside Binary Search Classs from previous section
    BFS() {
        let queue = [];
        let list = [];
        queue.push(this.root);
        while (queue.length != 0) {
            let node = queue.shift();
            list.push(node.data);
            if(node.left != null)queue.push(node.left)
            if(node.right != null)queue.push(node.right)
        }
        return list
    }
```

## DFS:

We implement DFS recursively. When we encounter a node, we can do things in three different ways

1. PreOrder:

	1. Add the node value to the list.
	2. Encounter the left node
	3. Encounter the right node

2. PostOrder
	
	1. Encounter the left node
	2. Encounter the right node
	3. Add the node value to the list

3. InOrder
	
	1. Encounter the left node
	2. Add the node value to the list
	3. Encounter the right node

```javascript
// Inside Binary Search Classs from previous section
    DFSPreOrder() {
        let list = [];

        function searchRecursive(node) {
            list.push(node.data);
            if (node.left != null) searchRecursive(node.left)
            if (node.right != null) searchRecursive(node.right)
        }
        searchRecursive(this.root);
        return list;
    }
    DFSPostOrder() {
        let list = [];

        function searchRecursive(node) {
            if (node.left != null) searchRecursive(node.left)
            if (node.right != null) searchRecursive(node.right)
            list.push(node.data);
        }
        searchRecursive(this.root);
        return list;
    }
    DFSInOrder() {
        let list = [];

        function searchRecursive(node) {
            if (node.left != null) searchRecursive(node.left)
            list.push(node.data);
            if (node.right != null) searchRecursive(node.right)
        }
        searchRecursive(this.root);
        return list;
    }
```

## BFS vs DFS
Time complexity for all four methods is same as we visit all the nodes once. But BFS takes more memory if we have a really dense tree due to the queue. When traversing, BFS stores the width in the memory whereas DFS stores the depth in the memory.