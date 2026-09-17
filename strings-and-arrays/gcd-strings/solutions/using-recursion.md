**Approach:**

Uses recursion to check if a valid GCD is present for the strngs. Has two base conditions; first, the string concatenated should equal the string concatenated the other way. Second if both strings are equal either of them is the GCD. The recursive step is to subtract the smaller string from bigger string.

| Metric | Complexity                                              |
| ------ | ------------------------------------------------------- |
| Time   | O((len(str1) + len(str2)) * min(len(str1), len(str2))) |
| Space  | O(len(str1) + len(str2) + slicing string memory)        |

The algorithm concatenates string and compares them for the base condition which results in the tike complexity of len(str1) + len(str2) which is costliest in first iteration and decreases gradually as we the smaller string from larger one. The space complexity is mainly calculated based on the recursive call stack and the slicing which creates new strings. The function calls itself recursively for min(len(str1) + len(str2)). The sliced strings add up to the calculations (even though the unused strings are GCed). 

**Code:**

```JavaScript
var gcdOfStrings = function(str1, str2) {

    if (str1 + str2 !== str2 + str1) return ""; 
  
    if (str1 === str2) return str1; 
  
    if (str1.length > str2.length) {
        return gcdOfStrings(str1.slice(str2.length), str2);
    } else {
        return gcdOfStrings(str1, str2.slice(str1.length));
    }
};
```
