### Lesson 01 `Binary Gap` (calculate max gap of '0' in binary numbers)

```js
function solution(N) {
    let binaryNumbers = N.toString(2);
    let maxGap = 0;
    let currentGap = 0;

    for (let digit of binaryNumbers) {
        // https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...of
        if (digit === '0') {
            currentGap++;
        } else {
            maxGap = Math.max(maxGap, currentGap) //function returns the largest of the zero or more numbers
            // https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/max)
            currentGap = 0;
        }
    }
    return maxGap;
}

console.log(solution(1041)) 
// binary = 10000010001; maxGap = 5;
console.log(solution(32)) 
// binary = 100000; maxGap = 0;
console.log(solution(529)) 
// binary = 1000010001; maxGap = 4;
```

### Lesson 02 `Cyclic Rotation` (Rotate an array to the right by a given number of steps)

```js
function solution(A, K) {
    for (i = 0; i < K; i++) {
        A.unshift(A.pop());
    }
    return A;
}

// The unshift() method adds one or more elements to the beginning of an array and returns the new length of the array.
// https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/unshift
// The pop() method removes the last element from an array and returns that element. This method changes the length of the array.
// https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/pop

A = [3, 8, 9, 7, 6]
K = 3
console.log(solution(A, K)) 
// [9, 7, 6, 3, 8]
```


