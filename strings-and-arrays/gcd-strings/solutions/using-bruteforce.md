**Approach:**

Checks if a number is a palindrome by reversing only the second half of the number and comparing it to the first half. This prevents integer overflow errors that could happen if you reversed the entire number.

| Metric | Complexity                        |
| ------ | --------------------------------- |
| Time   | O(len(str1) x len(str2))          |
| Space  | O(len(shorter string))            |

The algorithm has O(len(str1) x len(str2)) time complexity as it relies on nested loop iterations for coparing the candidate within two strings. The space complexity is O(len(shorter string)) because the code slices new string for the candidate out of the shorter string for each iteration.

**Code:**

```JavaScript
var gcdOfStrings = function(str1, str2) {
    // 1. Identify which string is bigger and which is shorter
    let bigger = str2;
    let shorter = str1;
    if (str1.length > str2.length) {
        bigger = str1;
        shorter = str2;
    }

    // 2. Start from the maximum possible length and look for divisors
    let j = shorter.length;
    while (j > 0) {
        // A valid GCD string length must perfectly divide both total lengths
        if (bigger.length % j === 0 && shorter.length % j === 0) {
            let candidate = shorter.slice(0, j);
            let isGcd = true;

            // 3. Verify if 'candidate' can completely reconstruct the 'bigger' string
            let i = 0;
            while (i < bigger.length) {
                if (bigger.slice(i, i + j) !== candidate) {
                    isGcd = false;
                    break;
                }
                i += j;
            }

            // 4. Verify if 'candidate' can completely reconstruct the 'shorter' string
            let k = 0;
            while (k < shorter.length) {
                if (shorter.slice(k, k + j) !== candidate) {
                    isGcd = false;
                    break;
                }
                k += j;
            }

            // If it successfully validated both strings, it's our answer
            if (isGcd) {
                return candidate;
            }
        }
        j--; // Decrement to try the next longest length
    }

    return "";
};
```
