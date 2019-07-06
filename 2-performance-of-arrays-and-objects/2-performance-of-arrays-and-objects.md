# Performance of Objects and Arrays

## Objects
Given a key, that specific key value pair of the object can be accessed in constant time.

1. Searching **O(n)**: Search if a value exists in the object
2. Accessing **O(1)**: Return the value given a key
3. Deleting **O(1)**: Removal of key value pair given a key
4. Insertion **O(1)**: Insertion of a new key value pair

### Object Methods
Consider  a ```banana``` object:

```javascript
let banana = {
	color : "yellow",
	taste : "sweet",
	calories : 100,
	isFav : true
}
```
1. Get an array of all the keys **O(n)**
```javascript
Object.keys(banana);
// ["color", "taste", "calories", "isFav"]
// O(n) as we need to access all the keys
```
2. Get an array of all the values **O(n)**
```javascript
Object.values(banana);
// ["yellow", "sweet", 100, true]
// O(n) as we need to access all the values
```
3. Get all the key-value pair **O(n)**
```javascript
Object.entries(banana);
// [["color", "yellow"], ["taste", "sweet"], ["calories", 100], ["isFav", true]]
// O(n) as we need to access all the key-value pairs
```
4. Check if a key exists **O(1)**
```javascript
banana.hasOwnProperty("color");
// true
banana.hasOwnProperty("yellow");
// false
```

## Arrays
Given an index, the thing at that index can be accessed in constant time.

1. Searching **O(n)**: Search if a value exists in the array
2. Accessing **O(1)**: Return the value at given index
3. Deleting:
* Delete last element: **O(1)**
* Delete first of middle element: **O(n)** (as it involves reassigning the indices)
4. Insertion:
* Insert last element: **O(1)**
* Insert first of middle element: **O(n)** (as it involves reassigning the indices)

### Array Methods:
Consider the ```groceries``` array:
```javascript
let groceries = ['milk', 'egg', 'bread', 'bananas'];
```

1. Insert and Delete at the last index **O(1)**:
```javascript
groceries.pop();
// ['milk', 'egg', 'bread']
groceries.push('apples');
//['milk', 'egg', 'bread', 'apples']
```
2. Insert and Delete at the first index **O(n)**:
```javascript
groceries.shift();
// [egg', 'bread', 'bananas']
groceries.unshift('beer');
//['beer', 'egg', 'bread', 'apples']
```
3. Insert and Delete at the middle of array **O(n)**:
```javascript
groceries.splice(1, 1, 'pizza', 'meat');
// ['milk', 'pizza', 'meat', 'bread', 'bananas']
```
4. Concatenation of two arrays **O(a + b)**:
```javascript
let a = [1, 2, 3];
let b = [4, 5, 6];
a.concat(b);
// [1, 2, 3, 4, 5, 6]
```
5. Slicing an array **O(n)**:
```javascript
let a = [1, 2, 3, 4, 5, 6];
a.slice(2, 4);
// [3, 4]
```
6. Sorting an array **O(nlong(n))**:
```javascript
let a = [4, 6, 1, 2, 5, 3]
a.sort();
// [1, 2, 3, 4, 5, 6]
```
7. Iteration over an array **O(n)**:
```javascript
let a = [1, 2, 3, 4, 5, 6]
a.forEach((value)=>console.log(value));
// 1
// 2
// 3
// 4
// 5
// 6
a.map((value)=>2*value);
// [2, 4, 6, 8, 10, 12]

a.filter((value)=>value%2==0);
// [2, 4, 6]

a.reduce((accumulator, value)=>accumulator + value);
// 21
```