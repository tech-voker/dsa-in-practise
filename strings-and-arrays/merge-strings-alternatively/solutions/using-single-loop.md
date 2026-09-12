**Approach:**

Merge two strings by iterating up to the length of longer string using a loop.

| Metric | Complexity                   |
| ------ | ---------------------------- |
| Time   | O(len(word1) + len(word(2))  |
| Space  | O(len(word1) + len(word(2))  |

The  time complexity is O(len(word1) + len(word(2)) , because the loop runs maximum of length of two words combine. The space complexity is O(N + M) to store the combined characters in the final returned string.

**Code:**

```javascript
var mergeAlternately = function(word1, word2) {

    const maxLength = Math.max(word1.length, word2.length);
    let output = [];
    for(let i =0; i<maxLength;i++){
        if(word1[i]){
            output.push(word1[i])
        }
        if(word2[i]){
            output.push(word2[i])
        }

    }
    return output.join('')
  
};
```

```Go
func mergeAlternately(word1 string, word2 string) string {
    bigger := word1
    if len(word2) > len(word1) {
        bigger = word2
    }
    i:= 0
    res := ""
    for i < len(bigger) {
        if i < len(word1) {
            res += string(word1[i])
        }
        if i < len(word2) {
            res+= string(word2[i])
        }
        i++
    }
    return res
}
```
