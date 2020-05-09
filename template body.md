## My Languages

- kyu: 7

You are given a dictionary/hash/object containing some languages and your test results in the given languages. Return the list of languages where your test score is at least 60, in descending order of the results.

Note: the scores will always be unique (so no duplicate values)

```javascript
Examples
{"Java": 10, "Ruby": 80, "Python": 65}    -->  ["Ruby", "Python"]
{"Hindi": 60, "Dutch" : 93, "Greek": 71}  -->  ["Dutch", "Greek", "Hindi"]
{"C++": 50, "ASM": 10, "Haskell": 20}     -->  []
```

My Solution:

```javascript
function myLanguages(results) {
  let filteredArray = [];

  for (let x in results) {
    if (results[x] >= 60) {
      filteredArray.push(x);
    }
  }

  let sortedArray = filteredArray.sort((a, b) => {
    return results[b] - results[a];
  });

  return sortedArray;
}
```

## Best Practice

```javascript
function myLanguages(results) {
  return Object.keys(results)
    .filter((r) => results[r] > 59)
    .sort((a, b) => results[b] - results[a]);
}
```

## Reflection

This kata was a fun use of objects and higher order methods. The directions are straight forward and easy to execute.
My biggest take away from this kata was looking through the comments and studying the best practice solution. It was so simple and elegant.

<!-- This challenge wasn't to difficult. I rationalized this problem with a similar lab I did called
Mars Rover from Ironhack. Similarly I had to keep track of where I was on a 2D Grid. I remember
that I had an object that kept track of N, S, E, W so i applied the same logic. I did get stuck and
had to look for some help and found [Snail](https://www.youtube.com/watch?v=EWYrxOsBX58) that was perfect explaination to my positioning difficulties. Essentially, I created an object where I kept track of my row
& Col upper and Lower bounds to trace my path as a snail. Worked to perfection. -->
