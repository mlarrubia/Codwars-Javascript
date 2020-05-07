## Josephus Survivor

- kyu: 5

In this kata you have to correctly return who is the "survivor", ie: the last element of a Josephus permutation.

Basically you have to assume that n people are put into a circle and that they are eliminated in steps of k elements, like this:

<pre>
josephus_survivor(7,3) => means 7 people in a circle;
one every 3 is eliminated until one remains
[1,2,3,4,5,6,7] - initial sequence
[1,2,4,5,6,7] => 3 is counted out
[1,2,4,5,7] => 6 is counted out
[1,4,5,7] => 2 is counted out
[1,4,5] => 7 is counted out
[1,4] => 5 is counted out
[4] => 1 counted out, 4 is the last element - the survivor!
</pre>

The above link about the "base" kata description will give you a more thorough insight about the origin of this kind of permutation, but basically that's all that there is to know to solve this kata.

Notes and tips: using the solution to the other kata to check your function may be helpful, but as much larger numbers will be used, using an array/list to compute the number of the survivor may be too slow; you may assume that both n and k will always be >=1.

My Solution:

```javascript
function josephusSurvivor(n, k) {
  let humans = [];
  for (let i = 1; i <= n; i++) {
    humans.push(i);
  }

  if (humans.length === 1) {
    return humans[0];
  }

  let step = k - 1;
  let x = step % humans.length;
  humans.splice(x, 1);
  while (humans.length > 1) {
    x = (x + step) % humans.length;
    humans.splice(x, 1);
  }
  return humans[0];
}
```

## Reflection

Josephus Survivor was a fun Kata that utilized the modulous operator. It's a great tool to use when wanting to say within range with a loop back. The best practice and clever solutions utilized 1 liner recursion. I am not confortable yet to implement recursion but I am currently taking an algorithm and data structures course that I hope to start utilizing the algorithms to solve my katas.

<!-- This challenge wasn't to difficult. I rationalized this problem with a similar lab I did called
Mars Rover from Ironhack. Similarly I had to keep track of where I was on a 2D Grid. I remember
that I had an object that kept track of N, S, E, W so i applied the same logic. I did get stuck and
had to look for some help and found [Snail](https://www.youtube.com/watch?v=EWYrxOsBX58) that was perfect explaination to my positioning difficulties. Essentially, I created an object where I kept track of my row
& Col upper and Lower bounds to trace my path as a snail. Worked to perfection. -->
