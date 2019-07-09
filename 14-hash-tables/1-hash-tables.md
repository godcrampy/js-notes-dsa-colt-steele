# Hash Tables
Objects and Maps in JavaScript, Dictionaries in Python, Maps in Dart are all Hash Table implementation.

## Working
Suppose we want to store a key value pair. Arrays are already key value pair implementation where keys are the indices. But suppose we want the key to be strings, in such case we need to use a hash table.
Consider the following object: ```{"pink" : "#ff6932", "cyan" : "#00fff"}```.
To store this data we need to use a hash function and an array. Suppose ```hash("pink")``` is 25. Thus we will store ```"#ff6932"``` at the 25 index of our array. Thus next time whenever we want to access the value of key ```"pink"```, we simply have to pass the key thru the hash function and the output index will be used to access the value from array.

## Hash Function
Hash function is a function that takes any data and converts it into a number.

**Properties of a good hash function:**
1. Fast (Constant Time)
2. Distributes numbers uniformly
3. Returns the same index for the same value everytime

Here's a hash  function
```javascript
// size is the size of array to be used
function hash(string, size) {
    let total = 0;
    for (char of string) {
        total += char.charCodeAt(0)
    }
    return total % size;
}
```
The problem with above function is a bad hash function as its O(n) and not that random.

```javascript
// removing O(n)
function hash(string, size) {
    let total = 0;
    for (let i = 0; i < Math.min(string.length, 100); i++) {
        total += string[i].charCodeAt(0)
    }
    return total % size;
}
```

```javascript
 // Increasing randomness
function hash(string, size) {
    let total = 0;
    const PRIME = 1327;
    for (let i = 0; i < Math.min(string.length, 100); i++) {
        total = (total * PRIME + string[i].charCodeAt(0)) % size;
    }
    return total;
}
```

> Pro Tip: Use Prime Number length for storing hash tables. https://qr.ae/TWtE8y

## Handling Collisions
What if two strings lead to a same hash?, We solve it by the following methods.

1. Separate Chaining:
Suppose ```hash("pink")``` and ```hash("orange")``` gives us a hash of 4. This method stores the key and hash in an array which are stored in an array at the specific index.

For Example: at index 4, we will have the following array after the above hashing: ```[["pink", "#ff6932"], ["orange", "#aa6666"]]```. Thus we will need to search the above array to get our value.

2. Linear Probing:
In this method, if an index is occupied, we look at the next unoccupied index and store our data there. So for the above example, if at index 4 we have ```[["pink", "#ff6932"]```, we will go to index 5 and if it is empty, we will store ```["orange", "#aa6666"]```. This method exhausts the hash array quickly.

## Implementation
```javascript
class HashTable {
    constructor() {
        this.keyMap = new Array(79);
    }
    _hash(string) {
        let total = 0;
        const PRIME = 1327;
        for (let i = 0; i < Math.min(string.length, 100); i++) {
            total = (total * PRIME + string[i].charCodeAt(0)) % 79;
        }
        return total;
    }

    set(key, value) {
        let hash = this._hash(key);
        if (this.keyMap[hash] == undefined)
            this.keyMap[hash] = [
                [key, value]
            ];
        else this.keyMap.push([key, value]);
    }

    get(key) {
        let hash = this._hash(key);
        let chain = this.keyMap[hash];
        for (pair of chain)
            if (pair[0] === key) return pair[1];
        return undefined;
    }
    pairs() {
        let pairs = [];
        for (let i = 0; i < 79; i++)
            if (banana.keyMap[i] != undefined)
                for (let pair of banana.keyMap[i]) pairs.push(pair)
        return pairs;
    }
}
```

## Complexity
* Insertion: O(1)
* Deletion: O(1)
* Access: O(1)