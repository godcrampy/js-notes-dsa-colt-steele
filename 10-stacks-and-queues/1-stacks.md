# Stacks

Last in First Out. Used in browser history, call stacks etc.

## Complexity
1. ```push``` and ```pop``` are constant time.

## Implementation

1. **Using Arrays**
```javascript
let a = [1, 2, 3];
a.push(4);
a.pop();
// 4
```

2. **Using Classes**
```javascript
class Node {
    constructor(data) {
        this.data = data;
        this.next = null;
    }
}

class Stack {
    constructor() {
        this.first = null;
        this.last = null;
        this.size = 0;
    }
    push(data) {
        let newNode = new Node(data);
        if (this.size === 0) {
            this.first = newNode;
            this.last = newNode;
        } else {
            newNode.next = this.last;
            this.last = newNode;
        }
        this.size++;
        return this.size;
    }
    pop() {
        if (this.size == 0) return undefined;
        let temp = this.last;
        this.last = this.last.next;
        this.size--;
        return temp;
    }
}
```