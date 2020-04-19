## Multiples of 3 or 5

- kyu: 6

If we list all the natural numbers below 10 that are multiples of 3 or 5, we get 3, 5, 6 and 9. The sum of these multiples is 23.

Finish the solution so that it returns the sum of all the multiples of 3 or 5 below the number passed in.

My Solution:

```javascript
function solution(number) {
  // map, filter, sort, reduce
  let total = 0;
  for (let i = 1; i < number; i++) {
    if (i % 3 == 0 || i % 5 == 0) {
      total += i;
    }
  }
  return total;
}
```

## Reflection

This challenge was pretty straight forward. Reminds me of the classic fizzbuzz problem. Initially, I wanted to use a higher order function to start getting comfortable with them. The problem was that my parameter was not an array, it was a number. With that being said, I resorted to a traditional for loop. After successfully completing the problem I refered to other solutions and found that my solution matched up with the "best practice". While I have my mindset to start getting comfortable using higher order functions it was humbling to realize early 2 things. The first is that I was not working with an array and the second that I do not need to try to complicate things.

<!-- This challenge wasn't to difficult. I rationalized this problem with a similar lab I did called
Mars Rover from Ironhack. Similarly I had to keep track of where I was on a 2D Grid. I remember
that I had an object that kept track of N, S, E, W so i applied the same logic. I did get stuck and
had to look for some help and found [Snail](https://www.youtube.com/watch?v=EWYrxOsBX58) that was perfect explaination to my positioning difficulties. Essentially, I created an object where I kept track of my row
& Col upper and Lower bounds to trace my path as a snail. Worked to perfection. -->
