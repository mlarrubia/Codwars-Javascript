## Building Blocks

- kyu: 7

Write a class Block that creates a block (Duh..)

##Requirements

The constructor should take an array as an argument, this will contain 3 integers of the form [width, length, height] from which the Block should be created.

Define these methods:

`getWidth()` return the width of the `Block`

`getLength()` return the length of the `Block`

`getHeight()` return the height of the `Block`

`getVolume()` return the volume of the `Block`

`getSurfaceArea()` return the surface area of the `Block`

##Examples

```javascript
  let b = new Block([2,4,6]) -> creates a `Block` object with a width of `2` a length of `4` and a height of `6`
  b.getWidth() // -> 2

  b.getLength() // -> 4

  b.getHeight() // -> 6

  b.getVolume() // -> 48

  b.getSurfaceArea() // -> 88
```

My Solution:

```javascript
class Block {
  constructor(data) {
    // ...
    this.width = data[0];
    this.length = data[1];
    this.height = data[2];
  }

  // ...
  getWidth() {
    return this.width;
  }

  getLength() {
    return this.length;
  }

  getHeight() {
    return this.height;
  }

  getVolume() {
    return this.height * this.length * this.width;
  }

  getSurfaceArea() {
    return (
      2 * (this.height * this.width) +
      2 * (this.height * this.length) +
      2 * (this.width * this.length)
    );
  }
}
```

<!--
## Reflection

Great use of higher order function .map() to iterate through a 2D array. Then it was using
a simple string method to return the value or \*; -->

<!-- This challenge wasn't to difficult. I rationalized this problem with a similar lab I did called
Mars Rover from Ironhack. Similarly I had to keep track of where I was on a 2D Grid. I remember
that I had an object that kept track of N, S, E, W so i applied the same logic. I did get stuck and
had to look for some help and found [Snail](https://www.youtube.com/watch?v=EWYrxOsBX58) that was perfect explaination to my positioning difficulties. Essentially, I created an object where I kept track of my row
& Col upper and Lower bounds to trace my path as a snail. Worked to perfection. -->
