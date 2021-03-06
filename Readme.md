### Lesson 01 `Binary Gap` (calculate max gap of '0' in binary numbers)

**JavaScript**
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

[**GoLang**](https://goplay.tools/snippet/IpL-fCWoyNr) :point_left:

```go
package solution

import (
	"fmt"
	"strconv"
)

var binaryNumbers = 0
var maxGap = 0
var currentGap int = 0

func Max(x, y int) int {
	if x > y {
		return x
	}
	return y
}

func Solution(N int) int {
	var binaryNumbers = strconv.FormatInt(int64(N), 2)
	// https://pkg.go.dev/strconv#FormatInt
	for _, digit := range binaryNumbers {
		// https://gobyexample.com/range
		if digit == '0' {
			currentGap++
		} else {
			maxGap = Max(maxGap, currentGap)
			currentGap = 0
		}
	}
	return maxGap
}

func main() {
	fmt.Println(Solution(1041))
	// binary = 10000010001; maxGap = 5;
}
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
[**GoLang**](https://play.golang.org/p/hioaVoVwgRH) :point_left:

```go
package solution

import "fmt"

func Solution(A []int, K int) []int {
	if len(A) <= 1 || K == 0 {
		return A
	}
	// a is the last element followed by the n elements
	// previously before the last element
	for i := 0; i < K; i++ {
		A = append(A[len(A)-1:], A[:len(A)-1]...)
	}
	return A
}
func main() {
	fmt.Println(Solution([]int{2,4,5,7}, 2))
	//[5 7 2 4]
}


Explanation:
package main

import (
	"fmt"
)

func main() {

	/*
	   Basically, we're getting the last value of the slice and assigning it as the first element.
	   After that, we get all the other values that originally came before it and put them in front of the last element (which is now the first one).

	   On how `[:]` works: https://tour.golang.org/moretypes/10
	*/

	// Given the original slice
	s := []int{2, 3, 4, 7}
	fmt.Println("s:", s)

	// We get the last value in s
	lastVal := s[len(s)-1:]
	fmt.Println(lastVal)

	// Then we get all the other values in s, except the last one
	valuesBeforeLastVal := s[:len(s)-1]

	// Finally, we assign s to receive the lastVal together with all the values that came before lastVal (valuesBeforeLastVal)
	s = append(lastVal, valuesBeforeLastVal...)

	fmt.Println("result:", s)
}

```
