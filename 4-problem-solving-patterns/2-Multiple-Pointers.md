# Multiple Pointers

Used when there is a linear **sorted** datastructure and the problem requires comparision between two members. Naive approach would give O(n<sup>2</sup>), while this method gives O(n)

This method involves using two pointers to traverse the array. One traverses from the left while the other traverses from the right.

## Example:
Write a function sumZero which accepts a sorted array of integers and return the number of pairs whose sum is zero.

### Naive Approach
1. Use a for loop to iterate over the array
2. For every number, iterate over the array again and find a partner number with sum zero

> Insight: The informatin that the array is sorted is not used

### Multiple Pointers + General Approach
#### Understand the Problem
1. Restate
> Write a function that takes a sorted array and returns the number of pairs such that the sum of the paired numbers is 0
2. Input
> a sorted array of numbers
3. Output
> Number of sumZero pairs
4. are input and output related
> Yes
5. Labels for useful fata
> Let's call the input array as simply array and the frequency of pair counter as pairCounter. Let the pointers be called left and righ

#### Explore Concrete Examples
1. Simple Case:
> [-3, -2, -1, 0, 1, 2, 3] => 3<br>
> the pointer should move towards each other until they cross each other
2. Boundary Case:
>[-4, 4, 5,6 , 34, 50] => 1<br>
> the pointer whose absolute value is higher should move
3. Empty case:
>[] =>0
4. Invalid Case:
> array assured

#### Break Down the Problem
```javascript
function sumZero(array){
	// define pointers and counter
	//while pointers dont cross:
		// compare numbers
		// if pair found move both pointers, counter++
		// else move the pointer with higher value
}
```

#### Solve/Simplify
```javascript
function sumZero(array){
	// define pointers and counter
	let left = 0;
	let right = array.length - 1;
	let pairCounter = 0;
	//while pointers dont cross:
	while(left < right){
		// compare numbers
		if(array[left] + array[right] === 0){
		// if pair found move both pointers, counter++
		pairCounter++;
		left++;
		right--;
		}
		else{
		// else move the pointer with higher value
		if(Math.abs(array[left] > Math.abs(right))){
			// left is larger
			left++;
		}
		else{
			right--;
		}
	}
	return pairCounter;
}
```

#### Look Back and Refactor
1. Does it work?
```javascript
//Corrected code
function sumZero(array) {
    // define pointers and counter
    let left = 0;
    let right = array.length - 1;
    let pairCounter = 0;
    //while pointers dont cross:
    while (left < right) {
        // compare numbers
        if (array[left] + array[right] === 0) {
            // if pair found move both pointers, counter++
            pairCounter++;
            left++;
            right--;
        } else {
            // else move the pointer with higher value
            if (Math.abs(array[left]) > Math.abs(array[right])) {
                // left is larger
                left++;
            } else {
                right--;
            }
        }
    }
    return pairCounter;
}
```
2. Other ways to approach problem?
> Naive way or two for loops
3. Other ways to approach smaller parts
> Not sure
4. Is code Readable
> Mostly
5. Refactor
```javascript
function sumZero(array) {
    let left = 0;
    let right = array.length - 1;
    let pairCounter = 0;
    //while pointers dont cross:
    while (left < right) {
        // compare numbers
        if (array[left] + array[right] === 0) {
            // if pair found move both pointers, counter++
            pairCounter++;
            left++;
            right--;
        } else {
            // move the pointer with higher value
            Math.abs(array[left]) > Math.abs(array[right]) ? left++ : right--;
        }
    }
    return pairCounter;
}
```