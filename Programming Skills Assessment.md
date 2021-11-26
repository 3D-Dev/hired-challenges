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
