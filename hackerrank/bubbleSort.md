## Bubble Sort | Hackerrank
Consider the following version of Bubble Sort:

    for (int i = 0; i < n; i++) {
	    for (int j = 0; j < n - 1; j++) {
	        // Swap adjacent elements if they are in decreasing order
	        if (a[j] > a[j + 1]) {
	            swap(a[j], a[j + 1]);
	        }
	    }
	}

Given an array of integers, sort the array in ascending order using the  _Bubble Sort_  algorithm above. Once sorted, print the following three lines:

1.  `Array is sorted in numSwaps swaps.`, where _numSwaps_ is the number of swaps that took place.
2.  `First Element: firstElement`, where  _firstElement_ is the _first_ element in the sorted array.
3.  `Last Element: lastElement`, where  _lastElement_  is the  _last_  element in the sorted array.

**Hint:**  To complete this challenge, you must add a variable that keeps a running tally of  _all_  swaps that occur during execution.

**Example**
_a = [6, 4, 1]_

```
swap    a       
0       [6,4,1]
1       [4,6,1]
2       [4,1,6]
3       [1,4,6]
```
The steps of the bubble sort are shown above. It took _3_ swaps to sort the array. Output is:
```
Array is sorted in 3 swaps.  
First Element: 1  
Last Element: 6
```
**Function Description**

Complete the function  _countSwaps_  in the editor below.

countSwaps has the following parameter(s):

-   _int a[n]:_  an array of integers to sort

**Prints**

Print the three lines required, then return. No return value is expected.

**Input Format**

The first line contains an integer,  _n_, the size of the array  _a_.  
The second line contains  _n_ space-separated integers _a[i]_.

**Output Format**

**Sample Input 0**
```
STDIN   Function
-----   --------
3       a[] size n = 3
1 2 3   a = [1, 2, 3]
```
**Sample Output 0**
```
Array is sorted in 0 swaps.
First Element: 1
Last Element: 3
```
**Explanation 0**  
The array is already sorted, so swaps take place.

**Sample Input 1**
```
3
3 2 1
```
**Sample Output 1**
```
Array is sorted in 3 swaps.
First Element: 1
Last Element: 3
```
**Explanation 1**  
The array is  _not sorted_, and its initial values are: _{3, 2, 1}_ . The following  _3_ swaps take place:
1. _{3, 2, 1}_ -> _{2, 3, 1}_ 
2.  _{2, 3, 1}_ -> _{2, 1, 3}_
3.  _{2, 1, 3}_ -> _{1, 2, 3}_
At this point the array is sorted and the three lines of output are printed to stdout.

**First:**
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
 * Complete the 'countSwaps' function below.
 *
 * The function accepts INTEGER_ARRAY a as parameter.
 */

function countSwaps(a) {
  let n = a.length;
  let numberOfSwaps = 0;
   for (let i = 0; i < n; i++) {   
    for (let j = 0; j < n - 1; j++) {
        // Swap adjacent elements if they are in decreasing order
        if (a[j] > a[j + 1]) {
            let swap = a[j +1];
            a[j+1]=a[j];
            a[j]=swap;
          numberOfSwaps++;
        }
    }
}
  console.log(`Array is sorted in ${numberOfSwaps} swaps.`)
  console.log(`First Element: ${a[0]}`)
  console.log(`Last Element: ${a[n-1]}`)
  return;
}



function main() {
    const n = parseInt(readLine().trim(), 10);

    const a = readLine().replace(/\s+$/g, '').split(' ').map(aTemp => parseInt(aTemp, 10));

    countSwaps(a);
}
```
