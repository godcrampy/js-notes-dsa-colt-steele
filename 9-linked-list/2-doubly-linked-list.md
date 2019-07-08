# Double Linked List
Collection of nodes each node containing a value and pointer to the next and the previous node.

> If a parameter is not passed to a function, that parameter gets the value of undefined.
>https://www.freecodecamp.org/news/copying-stuff-in-javascript-how-to-differentiate-between-deep-and-shallow-copies-b6d8c1ef09cd/

## Complexity
1. Search: O(n)
2. Access: O(n)
3. Delete: O(n) or O(1)
4. Insert: O(n) or O(1)

> Faster than or same speed as singly linked list

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

## Implemetation
```javascript
class Node {
    constructor(data) {
        this.data = data;
        this.previous = null;
        this.next = null;

    }
}

class DoublyLinkedList {
    constructor() {
        this.head = null;
        this.tail = null;
        this.length = 0;
    }

    push(data) {
        let newNode = new Node(data);
        if (this.length === 0) {
            this.head = newNode;
        } else {
            this.tail.next = newNode;
            newNode.previous = this.tail;
        }
        this.tail = newNode;
        this.length++;
        return this.length;
    }
    pop() {
        let final;
        if (this.length === 0) final = null;
        else if (this.length === 1) {
            final = this.head.data;
            this.head = null;
            this.tail = null;
            this.length = 0;
        } else {
            final = this.tail.data;
            this.tail = this.tail.previous;
            this.tail.next = null;
            this.length--;
        }
        return final;
    }
    shift() {
        let final;
        if (this.length === 0) final = null;
        else if (this.length === 1) {
            final = this.head.data;
            this.head = null;
            this.tail = null;
            this.length = 0;
        } else {
            final = this.head.data;
            this.head = this.head.next;
            this.head.previous = null;
            this.length--
        }
        return final;
    }
    unshift(data) {
        let newNode = new Node(data);
        if (this.length === 0) {
            this.tail = newNode;
        } else {
            this.head.previous = newNode;
            newNode.next = this.head;
        }
        this.head = newNode;
        this.length++;
        return this.length;
    }
    get(index) {
        if (index < 0 || index >= this.length) return null;
        let iterator;
        if (index > this.length / 2) {
            // Traverse from behind
            iterator = this.tail;
            let iteratorPosition = this.length - 1;
            while (iteratorPosition != index) {
                iterator = iterator.previous;
                iteratorPosition--;
            }
        } else {
            //travers from front
            iterator = this.head;
            let iteratorPosition = 0;
            while (iteratorPosition != index) {
                iterator = iterator.next;
                iteratorPosition++;
            }
        }
        return iterator;
    }
    set(index, data) {
        let iterator = this.get(index);
        if (!iterator) return false;
        iterator.data = data;
        return true;
    }
    insert(index, data) {
        let previousNode = this.get(index - 1);
        let nextNode = this.get(index);
        let newNode = new Node(data);
        if (index === 0 || this.length === 0) this.unshift(data)
        else if (index === this.length) this.push(data);
        else {
            previousNode.next = newNode;
            newNode.previous = previousNode;
            newNode.next = nextNode;
            nextNode.previous = newNode;
            this.length++;
        }
        return this.length;
    }
    remove(index) {
        if (index < 0 || index >= this.length) return undefined;
        if (index === 0) this.shift()
        else if (index === this.length - 1) this.pop()
        else {
            let final = this.get(index).data;
            let previousNode = this.get(index - 1);
            let nextNode = this.get(index + 1);
            previousNode.next = nextNode;
            nextNode.previous = previousNode;
            this.length--;
            return final;
        }
    }
    reverse() {
        let iterator = this.head;
        while(iterator){
            let temp = iterator.next;
            iterator.next = iterator.previous;
            iterator.previous = temp;
            iterator = iterator.previous;
        }
        let temp = this.head;
        this.head = this.tail;
        this.tail = temp;
    }
    traverse() {
        let iterator = this.head;
        while (iterator) {
            console.log(iterator.data);
            iterator = iterator.next;
        }
        return this.length;
    }
}
```