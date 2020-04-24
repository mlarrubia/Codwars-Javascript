## Robotic Tattoo Removal

- kyu: 7

Sometimes people get tattoos, sometimes they wish they hadn't, sometimes the tattoos must go. Lets create a robot that can remove tattoos.

Your robot function accepts one array argument called skinScan. I have supplied an example array below.

[
[' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' '],
[' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' '],
[' ',' ','X','X',' ',' ',' ','X','X',' ',' '],
[' ','X',' ',' ','X',' ','X',' ',' ','X',' '],
[' ','X',' ',' ',' ','X',' ',' ',' ','X',' '],
[' ','X',' ',' ',' ','X',' ',' ',' ','X',' '],
[' ','X',' ',' ',' ',' ',' ',' ',' ','X',' '],
[' ','X',' ',' ',' ',' ',' ',' ',' ','X',' '],
[' ','X',' ',' ',' ',' ',' ',' ',' ','X',' '],
[' ',' ','X',' ',' ',' ',' ',' ','X',' ',' '],
[' ',' ',' ','X',' ',' ',' ','X',' ',' ',' '],
[' ',' ',' ',' ','X',' ','X',' ',' ',' ',' '],
[' ',' ',' ',' ',' ','X',' ',' ',' ',' ',' '],
[' ',' ',' ',' ',' ','X',' ',' ',' ',' ',' '],
[' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' '],
[' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ']
]

Your task is to create a function for the robot function that will zap away the Xs and replace them with \*s. Any array values that are not Xs must be left alone. Below is what skinScan should look like after the tattoo has been removed.

[
[' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' '],
[' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' '],
[' ',' ','*','*',' ',' ',' ','*','*',' ',' '],
[' ','*',' ',' ','*',' ','*',' ',' ','*',' '],
[' ','*',' ',' ',' ','*',' ',' ',' ','*',' '],
[' ','*',' ',' ',' ','*',' ',' ',' ','*',' '],
[' ','*',' ',' ',' ',' ',' ',' ',' ','*',' '],
[' ','*',' ',' ',' ',' ',' ',' ',' ','*',' '],
[' ','*',' ',' ',' ',' ',' ',' ',' ','*',' '],
[' ',' ','*',' ',' ',' ',' ',' ','*',' ',' '],
[' ',' ',' ','*',' ',' ',' ','*',' ',' ',' '],
[' ',' ',' ',' ','*',' ','*',' ',' ',' ',' '],
[' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' '],
[' ',' ',' ',' ',' ','*',' ',' ',' ',' ',' '],
[' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' '],
[' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ']
]

My Solution:

```javascript
function robot(skinScan) {
  return skinScan.map((row) => {
    return row.map((col) => {
      return col.indexOf("X") >= 0 ? "*" : col;
    });
  });
}
```

## Reflection

Great use of higher order function .map() to iterate through a 2D array. Then it was using
a simple string method to return the value or \*;

<!-- This challenge wasn't to difficult. I rationalized this problem with a similar lab I did called
Mars Rover from Ironhack. Similarly I had to keep track of where I was on a 2D Grid. I remember
that I had an object that kept track of N, S, E, W so i applied the same logic. I did get stuck and
had to look for some help and found [Snail](https://www.youtube.com/watch?v=EWYrxOsBX58) that was perfect explaination to my positioning difficulties. Essentially, I created an object where I kept track of my row
& Col upper and Lower bounds to trace my path as a snail. Worked to perfection. -->
