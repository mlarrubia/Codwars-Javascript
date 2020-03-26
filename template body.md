## Challange 5

Name: array.Diff

- kyu: 6
- Your goal in this kata is to implement a difference function, which subtracts one list from another and returns the result.

Examples

```javascript
    It should remove all values from list a, which are present in list b.
    arrayDiff([1,2],[1]) == [2]

    If a value is present in b, all of its occurrences must be removed from the other:
    arrayDiff([1,2,2,2,3],[2]) == [1,3]

```

My Solution:

```javascript
function arrayDiff(a, b) {
  let first = [...a];

  b.forEach(num1 => {
    for (let i = first.length - 1; i >= 0; i--) {
      if (num1 == first[i]) {
        first.splice(i, 1);
      }
    }
  });
  return first;
}
```
