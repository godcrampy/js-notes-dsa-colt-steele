# Singly Linked List
Collection of nodes each node containing a value and pointer to the next node.

>In JavaScript, ```undefined``` means a variable has been declared but has not yet been assigned a value.<br>
```null``` is an assignment value. It can be assigned to a variable as a representation of no value

>Javascript is garbage collected, you don't need to delete objects themselves - they will be removed when there is no way to refer to them anymore.

## Methods
1. ```push(data)```: Works same as ```push``` of array
2. ```pop()```: Works same as ```pop``` of array
3. ```shift()```: Works same as ```shift``` of array
4. ```unshift(data)```: Works same as ```unshift``` of array
5. ```get(index)```: Gets the node at given index
6. ```set(index)```: Sets the node data at given index
7. ```insert(index, data)```: Inserts a node with given data at the given index
8. ```remove(index)```: Removes the node at the index
9. ```reverse()```: Reverses the list
10. ```traverse()```: Logs the list on the console


## Implementation
```javascript
class Node {
    constructor(data) {
        this.data = data;
        this.next = null;
    }
}

class SinglyLinkedList {
    constructor() {
        this.length = null;
        this.head = null;
        this.tail = null;
    }

    push(data) {
        let newNode = new Node(data);
        if (!this.head) {
            // Empty list
            this.head = newNode;
            this.tail = newNode;
        } else {
            this.tail.next = newNode;
            this.tail = newNode;
        }
        this.length++;
        return this.length;
    }
    pop() {
        if (!this.length) return undefined;
        // Find the second last node
        let iterator = this.head;
        while (iterator.next != this.tail) {
            iterator = iterator.next;
        }
        let final = this.tail.data;
        this.tail = iterator;
        this.tail.next = null;
        this.length--;
        if (this.length === 0) {
            this.head = null;
            this.tail = null;
        }
        return final
    }
    shift() {
        if (!this.length) return undefined;
        let newHead = this.head.next;
        let final = this.head.data;
        this.head = newHead;
        this.length--;
        if (this.length === 0) {
            this.head = null;
            this.tail = null;
        }
        return final;
    }
    unshift(data) {
        let newHead = new Node(data)
        if (this.length === 0) {
            this.head = newHead;
            this.tail = newHead;
        } else {
            newHead.next = this.head;
            this.head = newHead;
        }
        this.length++;
        return this.length;
    }
    traverse() {
        let iterator = this.head;
        while (iterator) {
            console.log(iterator.data);
            iterator = iterator.next;
        }
    }
    get(index = 0) {
        let iteratorPostion = 0;
        let iterator = this.head;
        if (index >= this.length || index < 0) return null
        while (iteratorPostion != index) {
            iterator = iterator.next;
            iteratorPostion++;
        }
        return iterator;
    }
    set(index = 0, data = undefined) {
        let iterator = this.get(index);
        if (!iterator) return false;
        iterator.data = data;
        return true;
    }
    insert(index = 0, data = undefined) {
        let prevNode = this.get(index - 1);
        let nextNode = this.get(index);
        let newNode = new Node(data);
        if (this.length === 0 || !nextNode) this.push(data)
        else if (!prevNode) this.unshift(data)
        else {
            prevNode.next = newNode;
            newNode.next = nextNode;
            this.length++;
        }
        return this.length;
    }
    remove(index = 0) {
        let prevNode = this.get(index - 1);
        let nextNode = this.get(index + 1);
        let currentNode = this.get(index);
        if (this.length === 0) return null;
        else if (!prevNode) this.shift()
        else if (!nextNode) this.pop()
        else {
            prevNode.next = nextNode;
            this.length--;
            return currentNode.data;
        }
    }
    reverse() {
        // flip head and tail
        let temp = this.head;
        this.head = this.tail;
        this.tail = temp;
        let node = this.tail;
        let prevNode = null;
        let nextNode = node.next;
        while (node != null) {
            node.next = prevNode;
            prevNode = node;
            node = nextNode;
            if (node != null) nextNode = node.next;
        }
    }
}
```