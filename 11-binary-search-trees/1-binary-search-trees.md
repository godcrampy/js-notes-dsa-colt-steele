# Binary Search Trees

## Trees
Trees are a data structure where the nodes are in a parent-child realtionship. They are non-linear unlike arrays and linked lists. Each parent in a tree may have multiple children but each child must have single aprent only. Singly linked list is a special case of tree. Nodes must point at their children only and not their siblings ie must go farther from the root. Root is a node with no parent. There is only one node in a tree.

![Tree](./htmltree.png)

### Definitions
1. **Root**: Topmost Node of tree with no parents
2. **Child**: A node directly connected to a node while moving away from the root node
3. **Parent**: The node to which child is connected to
4. **Siblings**: Nodes with same parents
5. **Leaf**: Nodes with no children
6. **Edge**: The connection between parent and child node

### Use
1. HTML DOM
2. Network Structure
3. Syntax Tree
4. Directory Structure
5. JSON

## Binary Tree
Subset of trees. Every node can have atmost _two_ children.

![Binary Tree](./binary_tree.svg)

## Binary Search Tree
Subset of Binary Trees. Every child to the left of a node is smaller than parent node and every child to the right is larger than the parent.

![Binary Search Tree](./binary_search_tree.svg)

### Complexity

1. Searching and Inserting: (Doubling sized increases one step)
* Best: O(1)
* Average: O(log(n))
* Worst: O(n)

> Worst occurs if the binary tree is one sided. That is every node has child only on the right(or left) side. In this case, it is basically a linked list.


### Implementation
```javascript
class Node {
    constructor(data) {
        this.left = null;
        this.right = null;
        this.data = data;
    }
}

class BinarySearchTree {
    constructor() {
        this.root = null;
    }
    insert(data) {
        let newNode = new Node(data)
        if (this.root === null) {
            this.root = newNode;
            return true;
        }
        let iterator = this.root;
        while (true) {
            if (data == iterator.data) return false;
            if (data > iterator.data) {
                // go to the right
                if (iterator.right == null) {
                    iterator.right = newNode;
                    break;
                }
                iterator = iterator.right;
            } else {
                // go to the left
                if (iterator.left == null) {
                    iterator.left = newNode;
                    break;
                }
                iterator = iterator.left;
            }
        }
        return true;
    }
    find(data) {
        let iterator = this.root;
        while (iterator != null) {
            if (data === iterator.data) return true;
            else if (data > iterator.data) iterator = iterator.right;
            else iterator = iterator.left;
        }
        return false;
    }
}
```