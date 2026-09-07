
**Approach:**

Checks if a number is a palindrome by reversing only the second half of the number and comparing it to the first half. This prevents integer overflow errors that could happen if you reversed the entire number.

| Metric | Complexity               |
| ------ | ------------------------ |
| Time   | O($\log_{10}(len(x))$) |
| Space  | O(1)                     |

The algorithm has a time complexity of O($\log_{10}(len(x))$)  because each loop iteration divides the input number by `10` to process one digit at a time, making the total number of operations roughly proportional to half the digits in \(n\). Concurrently, it maintains a space complexity of O(1) (constant space) because it only creates a single fixed integer variable to store the reversed digits, utilizing an identical, unchanging amount of memory regardless of how large the input size grows.

**Code:**

```JavaScript
var isPalindrome = function(x) {
      if (x < 0 || (x % 10 === 0 && x !== 0)) {
        return false;
    }
    let numeroInvertido = 0;
    while (x > numeroInvertido) {
        let ultimoDigito = x % 10;
        numeroInvertido = (numeroInvertido * 10) + ultimoDigito;
        x = Math.floor(x / 10);
    }
    return x === numeroInvertido || x === Math.floor(numeroInvertido / 10);
};
```

```Go
func isPalindrome(x int) bool {
    // Negative numbers and numbers ending in 0 (except 0 itself) cannot be palindromes
    if x < 0 || (x % 10 == 0 && x != 0) {
        return false
    }

    revertedNumber := 0
    for x > revertedNumber {
        revertedNumber = (revertedNumber * 10) + x % 10
        x /= 10
    }

    // When the length is an odd number, we can get rid of the middle digit by revertedNumber/10
    return x == revertedNumber || x == revertedNumber/10
}
```
