## Snail

- kyu: 4
  Given an n x n array, return the array elements arranged from outermost elements to the middle element, traveling clockwise.

Examples

array = [[1,2,3],
[4,5,6],
[7,8,9]]
snail(array) #=> [1,2,3,6,9,8,7,4,5]

For better understanding, please follow the numbers of the next array consecutively:

array = [[1,2,3],
[8,9,4],
[7,6,5]]
snail(array) #=> [1,2,3,4,5,6,7,8,9]

My Solution:

```javascript
function snail(array) {
  // returns empty array if size is 0
  if (array[0].length == 0) {
    return [];
  }

  let temp = [];

  // Keep track of where I am on the 2D grid
  let obj = {
    rs: 0,
    re: array.length - 1,
    cs: 0,
    ce: array.length - 1,
  };

  // Condition will run while all elements are not accounted for
  while (temp.length !== array.length * array[0].length) {
    // left -> right
    for (let i = obj.rs; i <= obj.re; i++) {
      temp.push(array[obj.cs][i]);
    }
    obj.cs++;

    // top -> bottom
    for (let i = obj.cs; i <= obj.ce; i++) {
      temp.push(array[i][obj.re]);
    }

    obj.re--;

    // right -> left
    for (let i = obj.re; i >= obj.rs; i--) {
      temp.push(array[obj.ce][i]);
    }
    obj.ce--;

    // bottom -> up
    for (let i = obj.ce; i >= obj.cs; i--) {
      temp.push(array[i][obj.rs]);
    }
    obj.rs++;
  }

  return temp;
}
```

## Reflection

This challenge wasn't to difficult. I rationalized this problem with a similar lab I did called
Mars Rover from Ironhack. Similarly I had to keep track of where I was on a 2D Grid. I remember
that I had an object that kept track of N, S, E, W so i applied the same logic. I did get stuck and
had to look for some help and found [Snail](https://www.youtube.com/watch?v=EWYrxOsBX58) that was perfect explaination to my positioning difficulties. Essentially, I created an object where I kept track of my row
& Col upper and Lower bounds to trace my path as a snail. Worked to perfection.
