## Challange 9

Name: Find the odd int

- kyu: 6
  Given an array, find the integer that appears an odd number of times.

There will always be only one integer that appears an odd number of times

Examples

```javascript
doTest([20, 1, 1, 2, 2, 3, 3, 5, 5, 4, 20, 4, 5], 5); // odd int 5
```

My Solution:

```javascript
function findOdd(arr) {
  let obj = {};

  // Creates key or increments count of key in array
  arr.forEach((x) => {
    x in obj ? obj[x]++ : (obj[x] = 1);
  });

  // Since there is only 1 occurence I use a for loop to find the odd int and return it
  for (x in obj) {
    if (obj[x] % 2 == 1) {
      return +x;
    }
  }
}
```
