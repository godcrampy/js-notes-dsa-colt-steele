# Radix Sort

Radix sort doesn't use comparisons for sorting instead uses properties of numbers. This sort can be done on integers only. The algorithm groups numbers according to the numbers at units, tens, hundreds and so on places.

>NOTE: primitive type variables like strings and numbers are always passed by value.
Arrays and Objects are passed by reference or by value based on these conditions:
> 1. if you are setting the value of an object or array it is Pass by Value.

```javascript
object1 = {prop: "car"};
array1 = [1,2,3];
```

>2. if you are changing a property value of an object or array then it is Pass by Reference.

```javascript
object1.prop = "car";
array1[0] = 9;
```
```javascript
function passVar(obj1, obj2, num) {
    obj1.prop = "laptop"; // will CHANGE original
    obj2 = { prop: "computer" }; //will NOT affect original
    num = num + 1; // will NOT affect original
}

var object1 = {
    prop: "car"
};
var object2 = {
    prop: "bike"
};
var number1 = 10;

passVar(object1, object2, number1);
console.log(object1); //output: Object {item:"laptop"}
console.log(object2); //output: Object {item:"bike"}
console.log(number1); //ouput: 10
```

## Complexity
> k is the base on numbers (10 in our case)
1. Time: O(kxn)
2. Space: O(k + n)

## Implementation
```javascript
function getDigit(number, place) {
    // returns the number at the given place 124, 3 => 1
    return Math.floor(Math.abs(number) / Math.pow(10, place)) % 10;
}

function digitCount(number) {
    if (number == 0) return 1;
    return Math.floor(Math.log10(Math.abs(number))) + 1;
}

function mostDigits(array) {
    let digits = 0;
    for (number of array)
        digits = Math.max(digitCount(number), number);
    return digits;
}

function radixSort(array) {
    let iterations = mostDigits(array);
    for (let i = 0; i < iterations; i++) {
        let bucket = Array.from({
            length: 10
        }, () => []);
        for (number of array)
            bucket[getDigit(number, i)].push(number);
        array = [].concat(...bucket)
    }
    return array;
}
```