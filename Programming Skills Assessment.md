#### Question1: Given a string of angle brackets, write a function that add brackets at the beginning and end of the string to make all brackets match. The angle brackets match if for every < there is a corresponding > and for every > there is a corresponding <.

The example input string : ><<><

The output string is <><<><>>

```
const process = (str) => {
  let count = 0;
  let leadingTag = 0;
  for (const char of str) {
    if (char === '>') {
      if (count === 0) {
        leadingTag++;
      } else {
        count--;
      }
    } else {
      count++;
    }
  }
  return '<'.repeat(leadingTag) + str + '>'.repeat(count);
};
```

#### Question2: Given a string, s, find the length of the longest substring that contains no repeated characters.
Example input:
S: “nndNFdfdf”
Example Output:
4

**Javascript:**
```
var lengthOfLongestSubstring = function (s) {
    // Base condition
    if (!s) {
        return 0;
    }
    // Starting index of the window
    let start = 0;
    // Ending index of the window
    let end = 0;
    // Maximum length of the substring
    let maxLength = 0;
    // Set to store the unique characters
    const uniqueCharacters = new Set();
    // Loop for each character in the string
    while (end < s.length) {
        if (!uniqueCharacters.has(s[end])) {
            uniqueCharacters.add(s[end]);
            end++;
            maxLength = Math.max(maxLength, uniqueCharacters.size);
        } else {
            uniqueCharacters.delete(s[start]);
            start++;
        }
    }
    return maxLength;
};

```
**Kotlin**
```
fun lengthOfLongestSubstring(s: String): Int {
    // Base condition
    if (s == "") {
        return 0
    }
    // Starting window index
    var start = 0
    // Ending window index
    var end = 0
    // Maximum length of substring
    var maxLength = 0
    // This set will store the unique characters
    val uniqueCharacters: MutableSet<Char> = HashSet()
    // Loop for each character in the string
    while (end < s.length) {
        if (uniqueCharacters.add(s[end])) {
            end++
            maxLength = maxLength.coerceAtLeast(uniqueCharacters.size)
        } else {
            uniqueCharacters.remove(s[start])
            start++
        }
    }
    return maxLength
}

```
