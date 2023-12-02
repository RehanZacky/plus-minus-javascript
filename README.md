# plus-minus-javascript
The provided code is an implementation 
of a JavaScript program that reads input from stdin (standard input), 
performs certain operations, and outputs the results to stdout (standard output).

Let's break down the main parts of the code:

1. **Input Handling:**
```javascript
process.stdin.resume();
process.stdin.setEncoding('utf-8');
```
This code activates stdin to receive input.
*setEncoding* is used to specify the input encoding as UTF-8.

2. *Input Reading:*
```javascript
process.stdin.on('data', function(inputStdin) {
    inputString += inputStdin;
});

process.stdin.on('end', function() {
    inputString = inputString.split('\n');
    main();
});
```
This code handles reading input from stdin. 
Input data is appended to the *inputString* variable on each 'data' event, 
and when the 'end' event occurs (indicating no more input data), 
the input is split into lines using '\n' as a delimiter, and the *main()* function is called.

3. *Function readLine:*
```javascript
function readLine() {
    return inputString[currentLine++];
}
```
This function is used to read a line from the previously split input and return that line.

4. *Function 'plusMinus':*
```javascript
function plusMinus(arr) {
    // ... (see explanation below)
}
```
This function takes an array of integers (arr), 
then calculates and prints the ratios of positive, negative, and zero elements in the array.

5. *Function main:*
```javascript
function main() {
    const n = parseInt(readLine().trim(), 10);

    const arr = readLine().replace(/\s+$/g, '').split(' ').map(arrTemp => parseInt(arrTemp, 10));

    plusMinus(arr);
}
```
This function reads the number of array elements from the first line of input, 
reads the array of integers from the second line, 
and then calls the *plusMinus* function with the read array.

In the plusMinus function:

- Variables positives, negatives, and zeros are used to store the counts of
  positive, negative, and zero elements.
- After iterating through the arr array,
  the ratios of these elements are calculated and printed to stdout.
  
This code appears to be designed to calculate the ratio of positive, 
negative, and zero elements in an array and print the results.

*Full Code:*
```javascript
'use strict';

process.stdin.resume();
process.stdin.setEncoding('utf-8');

let inputString = '';
let currentLine = 0;

process.stdin.on('data', function(inputStdin) {
    inputString += inputStdin;
});

process.stdin.on('end', function() {
    inputString = inputString.split('\n');

    main();
});

function readLine() {
    return inputString[currentLine++];
}

/*
 * Complete the 'plusMinus' function below.
 *
 * The function accepts INTEGER_ARRAY arr as parameter.
 */

function plusMinus(arr) {
     let positives = 0, negatives = 0, zeros = 0;
     const len = arr.length || 0;
      
     if (len > 0 && len <= 100) {
          arr.map((elem, key) => {
               if (elem > 0) {
                    positives++;
               } else if (elem < 0) {
                    negatives++; 
               } else {
                    zeros++;
               }
                  
               return elem; 
          }); 
     } 
     
     console.log((positives / len) || 0);
     console.log((negatives / len) || 0);
     console.log((zeros / len) || 0);      
}

function main() {
    const n = parseInt(readLine().trim(), 10);

    const arr = readLine().replace(/\s+$/g, '').split(' ').map(arrTemp => parseInt(arrTemp, 10));

    plusMinus(arr);
}
```

*input:*
```
6
-4 3 -9 0 4 1
```

*Print Result:*
```
0.5
0.3333333333333333
0.16666666666666666
```
