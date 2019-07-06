# Problem Solving Approach

## Algorithm
A _process_ or _sequence of tasks_ to accomplish a certain task

## General Approach
1. Understand the Problem
2. Explore Concrete Examples
3. Break it down
4. Solve/Simplify
5. Look Back and Refactor

## 1. Understand the problem:
1. Restate the problem in your own words.
2. What are the inputs? and their constraints?
3. What are the outputs? and their constraints?
4. Do I have enough informantion to determine the ouputs from inputs?(You may not know the answer to this right away!)
5. How should I label the important pieces of information that are a part of this problem?

## 2. Explore Concrete Examples:
1. Try a simple case
2. Try a boundary case
3. Try empty case (inputs not passed into function)
4. Try invalid cases (strings passed instead of numbers)

## 3. Break it Down:
* Break the problem into smaller tasks and write each task as a comment

## 4. Solve or Simplify:
* Solve each of the smaller tasks if you can.
* If you can't:
	1. Break down this task into even smaller task or
	2. Try ignoring the difficulty in the problem and solving the problem and then incorporating the difficulty back again

## 5. Look Back and Refactor:
1. See if your solution works on a sample case?
2. How can this problem be approached differently?
3. How can every smaller task approached differently?
4. Is the code understandable in a glance?
5. Clean the code

## Example:
Q: Write a function that takes in a string and returns counts of each charecter in the string as an object

### 1. Understand the Question:
1. Restate the function in your own words:
>Write down a function that takes a string as input, and return an object with the count of each charecter in the string

2. What are the inputs?
> The input is a string always

3. What are the outputs?
> The output needs to be an object with key of charecters paired up with their count as values

4. Are the inputs and outputs related?
> Yes.

5. How do I label the important pieces of information in the problem?
> Let's call the input as string and the output Object as table.

### 2. Explore Concrete Examples:
1. Simple
> "Hello" => {h : 1, e : 1, l : 2, o : 1}<br>
> Upper case and lowercase are same<br>
> 0 counts are not returned
2. Boundary:
> "Hello hi" => {h : 2, e : 1, l : 2, o : 1, i : 1}<br>
> Spaces don't count, only alphanumeric do
3. Empty:
> "" => {}
4. Invalid:
> No Invalid Cases will be provided

### 3. Break Down the Problem:
```javascript
function getCountObject(string){
	// define table
	// do the counting
		//Iterate over the string
		//if char is alpa numeric:
			// if char in table, value++
			// else add char to the table with value 1
	// return table
}
```
>TODO: Learn Regex !important
### 4. Solve or Simplify:
```javascript
function getCountObject(string){
	// define table
	let table = {};
	// do the counting
		//Iterate over the string
		for(char of table){
			//if char is alpa numeric:
			if(isAlphaNumeric(char)){
			// if char in table, value++
				if(table[char]){
					table[char]++;
				}
			// else add char to the table with value 1
				else{
					table[char] = 1;
				}
			}
		}
	// return table
	return table;
}
function isAlphaNumeric(char){
	if(/[a-z0-9]/.text(char)){
		return true;
	}
	return false;
}
```

### 5. Look Back and Refactor
1. Does it work?
```javascript
//Corrected Code
function getCountObject(string) {
    // define table
    let table = {};
    // do the counting
    //Iterate over the string
    for (char of string) {
        char = char.toLowerCase();
        //if char is alpa numeric:
        if (isAlphaNumeric(char)) {
            // if char in table, value++
            if (table[char]) {
                table[char]++;
            }
            // else add char to the table with value 1
            else {
                table[char] = 1;
            }
        }
    }
    // return table
    return table;
}

function isAlphaNumeric(char) {
    if (/[a-z0-9]/.test(char)) {
        return true;
    }
    return false;
}
```
2. How can this problem be approached differently?
> Maybe there is some builtin function which does this

3. How can the smaller parts be approached differently?
> 1. lowercase the whole string first
> 2. using ascii values instead of regex

4. Is this code understandable at glance?
> can be refactored

5. Refactor the code
```javascript
//Final Code
function getCountObject(string) {
    let table = {};
    string.toLowerCase();
    for (char of string) {
        if (isAlphaNumeric(char)) {
        	table[char] = ++table[char] || 1;
        }
    }
    // return table
    return table;
}

function isAlphaNumeric(char) {
    return /[a-z0-9]/.test(char);
}
```