### `Binary Gap` (calculate max gap of '0' in binary numbers)
```js
function solution(N) {
    // write your code in JavaScript (Node.js 8.9.4)
    let binaryNumbers = N.toString(2);
    let maxGap = 0;
    let currentGap = 0;

    for (let digit of binaryNumbers) {
        if (digit === '0') {
            currentGap++;
        } else {
            maxGap = Math.max(maxGap, currentGap)
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
