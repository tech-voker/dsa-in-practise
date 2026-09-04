**Approach:**

Harnesses two pointer approach by converting number into string. 

| Metric | Complexity |
| ------ | ---------- |
| Time   | O(len(x))  |
| Space  | O(len(x))  |

The approach first converts a number to a string, accounting for O(len(x)) time complexity and then iterates half the string atleast for palindrome identification, hence another O(len(x)/2). Total time complexity becomes O(len(x)).
Because a new string is created equivalent to the digits in number, the space complexity is O(len(x)).


**Code:**

```JavaScript
var isPalindrome = function(x) {
    let a = String(x)
    let i = 0;
    let j = a.length -1
    if(a.length == 2){
        return a[i] == a[j]
    }
    while(i != j && i <j) {
        if(a[i] !== a[j]){
            return false
        }
        i++
        j--
    }
    return true;
};
```

```Go
func isPalindrome(x int) bool {
    a := strconv.Itoa(x)
    i := 0
    j := len(a) - 1
    if len(a) == 2 {
        return a[i] == a[j]
    }
    for i != j && i < j {
        if a[i] != a[j] {
            return false
        }
        i++
        j--
    }
    return true
}
```
