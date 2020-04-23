## Pete, the baker

- kyu: 5

Pete likes to bake some cakes. He has some recipes and ingredients. Unfortunately he is not good in maths. Can you help him to find out, how many cakes he could bake considering his recipes?

Write a function cakes(), which takes the recipe (object) and the available ingredients (also an object) and returns the maximum number of cakes Pete can bake (integer). For simplicity there are no units for the amounts (e.g. 1 lb of flour or 200 g of sugar are simply 1 or 200). Ingredients that are not present in the objects, can be considered as 0.

Example
// must return 2
cakes({flour: 500, sugar: 200, eggs: 1}, {flour: 1200, sugar: 1200, eggs: 5, milk: 200});
// must return 0
cakes({apples: 3, flour: 300, sugar: 150, milk: 100, oil: 100}, {sugar: 500, flour: 2000, milk: 2000});

My Solution:

```javascript
function cakes(recipe, ingredients) {
  let hasIngredients = true;

  let recipeKey = [];

  for (let x in recipe) {
    recipeKey.push(x);
  }

  recipeKey.forEach((key) => {
    if (!(key in ingredients)) {
      // console.log("Test", key in ingredients)
      // return 0;
      hasIngredients = false;
    }
  });

  if (!hasIngredients) {
    return 0;
  }

  let max = 10000;

  recipeKey.filter((eachIngredient) => {
    // if(ingredients[eachIngredient]){
    // console.log("Test" + recipe[eachIngredient] + " " + ingredients[eachIngredient] + " " + ingredients[eachIngredient] / recipe[eachIngredient])
    let current = Math.floor(
      ingredients[eachIngredient] / recipe[eachIngredient]
    );
    if (current < max) {
      max = current;
    }
    // console.log(current)
    // }
  });

  return Number(max);
}
```

## Reflection

<!-- This challenge wasn't to difficult. I rationalized this problem with a similar lab I did called
Mars Rover from Ironhack. Similarly I had to keep track of where I was on a 2D Grid. I remember
that I had an object that kept track of N, S, E, W so i applied the same logic. I did get stuck and
had to look for some help and found [Snail](https://www.youtube.com/watch?v=EWYrxOsBX58) that was perfect explaination to my positioning difficulties. Essentially, I created an object where I kept track of my row
& Col upper and Lower bounds to trace my path as a snail. Worked to perfection. -->
