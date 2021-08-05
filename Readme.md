### Lesson 01 `Binary Gap` (calculate max gap of '0' in binary numbers)
JavaScript solution
------

```js
function solution(N) {
    let convetToBinary = 2
    let binaryNumbers = N.toString(convetToBinary);
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
