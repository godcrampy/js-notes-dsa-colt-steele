# Frequency Counters

If there is a loop in loop resulting in a time complexity of _O(n<sup>2</sup>)_, break down into two seperate for loops by making object structures and then use these structures to do the furthur manipulations as accessing objects is faster than accessing arrays and strings

## Example

Write a function same that accepts two arrays. The function should return true if every value in the array has it's corresponding value squared in the second array. The frequency values must be same.

 ### Naive Approach

 1. Iterate over first loop
 2. For every value in first loop, iterate over the second loop
 3. if the value in second loop is square of value in the first loop, delete that value in the second loop(to account for frequency as well)

 ### Frequency Counter + General Approach from previous chapter

 #### Understand the problem
 
 1. Restate the question in own words
 > There are two arrays. Return true if for every value the first array, there exists a unique square value in the second array. 

 2. What are the Inputs?
 > Two arrays of numbers

 3. What are the outputs?
 > Boolean

 4. Are Inputs and Outputs related?
 > Yes

 5. What labels should be given for important data
 > Let's call the first array as initialArray and the second array as finalArray. Let's call the two tables as initialTable and finalTable.

#### Explore Concrete Examples
1. Simple case
> [1, 2, 3], [1, 4, 9] => true] <br>
> Oreder does'nt matter

2. Boundary case
> [1, 1, 2], [1, 4, 1] => true <br>
> frequency does matter

3. Zero case
> [], [] => true

4. Invalid case
> always valid ie arrays

#### Break Down the Problem
```javascript
// Use Frequency counter approach to get two arrays first
function same(initialArray, finalArray){
	// make empty tables
	// copy array into tables
	// compare tables
	// return
}
```

#### Solve/Simplify
```javascript
// Use Frequency counter approach to get two arrays first
function same(initialArray, finalArray){
	// make empty tables
	// copy array into tables
	let initialTable = arrayToTable(initialArray);
	let finalTable = arrayToTable(finalArray);
	for(key in initialTable){
		if(initialTable[key] != finalTable[key**2]){
			return false;
		}
	}
	// compare tables
	return true;
}

function arrayToTable(array){
	let table = {};
	//[1, 1, 2, 3] => {1 : 2, 2: 1, 3 : 1}
	for(number of array){
		table[number] = ++table[number] || 1;
	}
	return table;
}
```

#### Look Back and Refactor
1. Does it run:
> Yes
2. Ways to approach the problem
> Naive : two for loops
3. Ways to apporach the parts
> NOt using the second function
4. Is the code understandable at first glance
> Mostly
5. Clean
```javascript
//Final Code
function same(initialArray, finalArray){
	// convert array to frequency tables
	let initialTable = arrayToTable(initialArray);
    let finalTable = arrayToTable(finalArray);
	// compare tables
	for(key in initialTable){
		if(initialTable[key] != finalTable[key**2]){
			return false;
		}
	}
	return true;
}

function arrayToTable(array){
	let table = {};
	//[1, 1, 2, 3] => {1 : 2, 2: 1, 3 : 1}
    array.forEach((value)=>table[value] = ++table[value] || 1);
	return table;
}
```