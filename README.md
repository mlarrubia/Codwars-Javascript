# Codwars Javascript

| Name                                                | Kata | Tags                                                                                                           | Solution                                          | Codewar Link                                                                                              |
| --------------------------------------------------- | ---- | -------------------------------------------------------------------------------------------------------------- | ------------------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| Snail                                               | 4    | Algoirthms Arrays                                                                                              | <[Solution](#Snail)>                              | <[link](https://www.codewars.com/kata/521c2db8ddc89b9b7a0000c1/javascript)>                               |
| Human readable duration format                      | 4    | Algorithms Formats Strings Dates/Time Formatting                                                               | <[Solution](#Human-readable-duration-format)>     | <[link](https://www.codewars.com/kata/52742f58faf5485cae000b9a/train/javascript)>                         |
| Break the Caesar                                    | 5    | Fundamentals Ciphers Algorithms Cryptography Security Encryption Decryption                                    | <[Solution](#Break-the-caesar)>                   | <[link](https://www.codewars.com/kata/598e045b8c13926d8c0000e8/train/python)>                             |
| Pete, the baker                                     | 5    | Algorithms                                                                                                     | <[Solution](#Pete,-the-baker)>                    | <[link](https://www.codewars.com/kata/525c65e51bf619685c000059/train/javascript)>                         |
| Extract the domain name from a URL                  | 5    | Fundamentals Parsing Algorithms Strings Regular Expressions Declarative Programming Advanced Language Features | <[Solution](#Extract-the-domain-name-from-a-URL)> | <[link](https://www.codewars.com/kata/514a024011ea4fb54200004b/javascript)>                               |
| Find the odd int                                    | 6    | Fundamentals                                                                                                   | <[Solution](#Find-the-odd-int)>                   | <[link](https://www.codewars.com/kata/54da5a58ea159efa38000836/train/javascript)>                         |
| Break camelCase                                     | 6    | Fundamentals Strings Formatting Algorithms                                                                     | <[Solution](#Break-camelCase)>                    | <[link](https://www.codewars.com/kata/5208f99aee097e6552000148/train/javascript)>                         |
| array.Diff                                          | 6    | Fundamentals Arrays                                                                                            | <[Solution](#array-differences)>                  | <[link](https://www.codewars.com/kata/array-dot-diff)>                                                    |
| Title Case                                          | 6    | Fundamentals, Strings, Parsing, Algorithms                                                                     | [Solution](#Title-case)                           | [link](https://www.codewars.com/kata/title-case)                                                          |
| Format a string of names like 'Bart, Lisa & Maggie' | 6    | Fundamentals, Strings, Formatting, Algorithms                                                                  | [Solution](#Format-a-string-of-names)             | [link](https://www.codewars.com/kata/format-a-string-of-names-like-bart-lisa-and-maggie/train/javascript) |
| Multiples of 3 or 5                                 | 6    | Algorithms Mathematics Numbers                                                                                 | <[Solution](#Multiples-of-3-or-5)>                | <[link](https://www.codewars.com/kata/514b92a657cdc65150000006/javascript)>                               |
| Building Blocks                                     | 7    | Fundamentals Object-Oriented Programming Basci Language Features                                               | <[Solution](#Building-Blocks)>                    | <[link](https://www.codewars.com/kata/55b75fcf67e558d3750000a3)>                                          |
| The highest profit wins!                            | 7    | Repetition, Decision, Arrays                                                                                   | [Solution](#The-highest-profit-wins)              | [link](https://www.codewars.com/kata/the-highest-profit-wins/train/javascript)                            |
| Robotic Tattoo Removal                              | 7    | Fundamentals Arrays Graphs Data Structures                                                                     | <[Solution](#Robotic-Tattoo-Removal)>             | <[link](https://www.codewars.com/kata/57658f3dedc6f7a751000e7b/train/javascript)>                         |
| Growing Plant                                       | 7    | Algorithms                                                                                                     | <[Solution](#Growing-Plant)>                      | <[link](https://www.codewars.com/kata/58941fec8afa3618c9000184)>                                          |
| Fake Binary                                         | 8    | Repetition, Decision, String Methods                                                                           | [Solution](#Fake-binary)                          | [link](https://www.codewars.com/kata/fake-binary/train/javascript)                                        |

## Extract the domain name from a URL

- kyu: 5

Write a function that when given a URL as a string, parses out just the domain name and returns it as a string. For example:

```javascript
domainName("http://github.com/carbonfive/raygun") == "github";
domainName("http://www.zombie-bites.com") == "zombie-bites";
domainName("https://www.cnet.com") == "cnet";
```

My Solution:

```javascript
function domainName(url) {
  if (url.includes("http://www.")) {
    let start = url.indexOf("www.") + 4;
    let startWord = url.substring(start);
    let end = startWord.indexOf(".");
    return url.substring(start, end + start);
  } else if (url.includes("http://")) {
    let start = url.indexOf("://") + 3;
    let end = url.indexOf(".");
    return url.substring(start, end);
  } else if (url.includes("https://www.")) {
    let start = url.indexOf("www.") + 4;
    let startWord = url.substring(start);
    let end = startWord.indexOf(".");
    return url.substring(start, end + start);
  } else if (url.includes("https://")) {
    let start = url.indexOf("://") + 3;
    let end = url.indexOf(".");
    return url.substring(start, end);
  } else if (url.includes("www.")) {
    let start = url.indexOf("www.") + 4;
    let end = url.lastIndexOf(".");
    return url.substring(start, end);
  } else if (!url.includes("http") || !url.includes("www.")) {
    let end = url.indexOf(".");
    return url.substring(0, end);
  }
}
```

## Reflection

Wow! I am almost embarassed to post my solution. My answer works fine, but i was just amazed at the simplicity of some of the other solutions. I am very familiar with the String method .replace it just did not come to mind. I think because initally, i had thought of using regex. I decided not to after starting a course about data structures and algorithms and going over Big O Notation. We observed some different methods of solving a problem and regex was really cumbersome on the resources. I will include the solution voted by codewar community as the best practice and most clever.

```javascript
function domainName(url) {
  url = url.replace("https://", "");
  url = url.replace("http://", "");
  url = url.replace("www.", "");
  return url.split(".")[0];
}
```

## Growing Plant

- kyu: 7

Each day a plant is growing by upSpeed meters. Each night that plant's height decreases by downSpeed meters due to the lack of sun heat. Initially, plant is 0 meters tall. We plant the seed at the beginning of a day. We want to know when the height of the plant will reach a certain level.

Example
For upSpeed = 100, downSpeed = 10 and desiredHeight = 910, the output should be 10.

After day 1 --> 100
After night 1 --> 90
After day 2 --> 190
After night 2 --> 180
After day 3 --> 280
After night 3 --> 270
After day 4 --> 370
After night 4 --> 360
After day 5 --> 460
After night 5 --> 450
After day 6 --> 550
After night 6 --> 540
After day 7 --> 640
After night 7 --> 630
After day 8 --> 730
After night 8 --> 720
After day 9 --> 820
After night 9 --> 810
After day 10 --> 910
For upSpeed = 10, downSpeed = 9 and desiredHeight = 4, the output should be 1.

Because the plant reach to the desired height at day 1(10 meters).

After day 1 --> 10
Input/Output
[input] integer upSpeed

A positive integer representing the daily growth.

Constraints: 5 ≤ upSpeed ≤ 100.

[input] integer downSpeed

A positive integer representing the nightly decline.

Constraints: 2 ≤ downSpeed < upSpeed.

[input] integer desiredHeight

A positive integer representing the threshold.

Constraints: 4 ≤ desiredHeight ≤ 1000.

[output] an integer

The number of days that it will take for the plant to reach/pass desiredHeight (including the last day in the total count).

My Solution:

```javascript
function growingPlant(upSpeed, downSpeed, desiredHeight) {
  //coding and coding..

  let height = 0;
  let count = 0;

  while (height <= desiredHeight) {
    count++;
    height += upSpeed;
    if (height >= desiredHeight) {
      return count;
    }
    height -= downSpeed;
  }
  count--;
  return count;
}
```

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

This challenge was pretty straight forward. Reminds me of the classic fizzbuzz problem. Initially, I wanted to use a higher order function to start getting comfortable with them. The problem was that my parameter was not an array, it was a number. With that being said, I resorted to a traditional for loop. After successfully completing the problem I refered to other solutions and found that my solution matched up with the "best practice". While I have my mindset to start getting comfortable using higher order functions it was humbling to realize early 2 things. The first is that I was not working with an array and the second that I do not need to try to complicate things

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

## Find the odd int

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

## Human readable duration format

- kyu: 4

The resulting expression is made of components like 4 seconds, 1 year, etc. In general, a positive integer and one of the valid units of time, separated by a space. The unit of time is used in plural if the integer is greater than 1.

The components are separated by a comma and a space (", "). Except the last component, which is separated by " and ", just like it would be written in English.

A more significant units of time will occur before than a least significant one. Therefore, 1 second and 1 year is not correct, but 1 year and 1 second is.

Different components have different unit of times. So there is not repeated units like in 5 seconds and 1 second.

A component will not appear at all if its value happens to be zero. Hence, 1 minute and 0 seconds is not valid, but it should be just 1 minute.

A unit of time must be used "as much as possible". It means that the function should not return 61 seconds, but 1 minute and 1 second instead. Formally, the duration specified by of a component must not be greater than any valid more significant unit of time.

Examples

```javascript
formatDuration(62); // returns "1 minute and 2 seconds"
formatDuration(3662); // returns "1 hour, 1 minute and 2 seconds"
```

My Solution:

```javascript
function formatDuration(sec) {
  let count = 0;
  let str = ``;

  // Returns now if zero seconds
  if (sec === 0) {
    return "now";
  }

  // Object to structure each input
  let obj = {
    year: Math.floor(sec / 31536000),
    day: Math.floor((sec % 31536000) / 86400),
    hour: Math.floor(((sec % 31536000) % 86400) / 3600),
    minute: Math.floor((((sec % 31536000) % 86400) % 3600) / 60),
    second: Math.floor((((sec % 31536000) % 86400) % 3600) % 60),
  };

  // Lets find out how many keys are >= 1
  for (x in obj) {
    if (obj[x] >= 1) {
      count++;
    } else {
      delete obj[x];
    }
  }

  // Lets build our return string
  for (x in obj) {
    // Possible problem
    count--;
    // plural
    if (obj[x] > 1) {
      str += `${obj[x]} ${x}s`;
    } else {
      str += `${obj[x]} ${x}`;
    }
    // comma
    if (count > 1) {
      str += `, `;
    }
    // and
    if (count == 1) {
      str += ` and `;
    }
  }
  return str;
}
```

## Break the Caesar

- kyu: 5
- The Caesar cipher is a notorious (and notoriously simple) algorithm for encrypting a message: each letter is shifted a certain constant number of places in the alphabet. For example, applying a shift of 5 to the string "Hello, world!" yields "Mjqqt, btwqi!", which is jibberish.

In this kata, your task is to decrypt Caesar-encrypted messages using nothing but your wits, your computer, and a set of the 1000 (plus a few) most common words in English in lowercase (made available to you as a preloaded variable named WORDS, which you may use in your code as if you had defined it yourself).

Given a message, your function must return the most likely shift value as an integer.

Examples

```python
  test.assert_equals(break_caesar("DAM? DAM! DAM."), 7)
  test.assert_equals(break_caesar("Mjqqt, btwqi!"), 5)
  test.assert_equals(break_caesar("Gur dhvpx oebja sbk whzcf bire gur ynml qbt."), 15)
```

My Solution:

```python
  import string

# Main function
def break_caesar(message):
  count = 0
  shift = 0
  for x in range(26):
    # returns the POSSIBLE decrypted (OG) message
    decryptedMessageRaw = decrypt(message, x)
    # Removes punctuation, got from StackOverFlow
    decryptedMessageFiltered = decryptedMessageRaw.translate(str.maketrans('', '', string.punctuation))

    arr = decryptedMessageFiltered.split(' ')
    # Returns number of matched words to the 1000 most common words in the english dictionary
    current = checkCount(arr)
    if(current > count):
      count = current
      shift = x

  return shift



def checkCount(arr):
  num = 0
  for x in arr:
    word = x.lower()
    # WORDS was an array of 1000 common english words
    if word in WORDS:
      num += 1
  return num


def decrypt(word, number):
  decryptedWord = ''
  for x in word:
    letter = x
    digitNumber = ord(letter);

    #   Lowercase 97 - 122
    if( digitNumber >=97 and digitNumber <= 122):
      if(digitNumber - number < 97):
        digitNumber = 123 - (abs((digitNumber - number) - 97))
      else:
        digitNumber = digitNumber - number
      letter = chr(digitNumber)
    # Uppercase 65 - 90
    elif(digitNumber >=65 and digitNumber <= 90):
      if(digitNumber - number < 65):
        # changed 65 to 64... IDK why
        digitNumber = 90 - (64 - abs(digitNumber - number))
      else:
        digitNumber = digitNumber - number
      letter = chr(digitNumber)
    decryptedWord += letter
  # print(decryptedWord)
  return decryptedWord



```

## Break camelCase

- kyu: 6
  Complete the solution so that the function will break up camel casing, using a space between words.

Examples

```javascript
solution("camelCasing") == "camel Casing";
```

My Solution:

```javascript
function solution(string) {
  return string.split(/(?=[A-Z])/).join(" ");
}
```

                         |

## array differences

- kyu: 6
  Your goal in this kata is to implement a difference function, which subtracts one list from another and returns the result.

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

  b.forEach((num1) => {
    // Start from back front so when I splice it does not affect indexing when everything shifts
    for (let i = first.length - 1; i >= 0; i--) {
      if (num1 == first[i]) {
        first.splice(i, 1);
      }
    }
  });
  return first;
}
```

## Title Case

- kyu: 6
  Write a function that will convert a string into title case, given an optional list of exceptions (minor words). The list of minor words will be given as a string with each word separated by a space. Your function should ignore the case of the minor words string -- it should behave in the same way even if the case of the minor word string is changed.

Examples

```javascript
titleCase("a clash of KINGS", "a an the of"); // should return: 'A Clash of Kings'
titleCase("THE WIND IN THE WILLOWS", "The In"); // should return: 'The Wind in the Willows'
titleCase("the quick brown fox"); // should return: 'The Quick Brown Fox'
```

My Solution:

```javascript
function titleCase(title, minorWords) {
  let mw;
  if (minorWords !== undefined) {
    mw = minorWords.split(" ");
  } else {
    mw = [];
  }

  let titleArray = title.split(" ");

  let temp = "";
  titleArray.forEach((word) => {
    let isMW = false;
    for (let i = 0; i < mw.length; i++) {
      if (word.toLowerCase() === mw[i].toLowerCase()) {
        isMW = true;
      }
    }
    if (isMW) {
      temp += word.toLowerCase() + " ";
    } else {
      temp +=
        word.charAt(0).toUpperCase() + word.substring(1).toLowerCase() + " ";
    }
  });

  let trimmed = temp.trim();
  let response = trimmed.charAt(0).toUpperCase() + trimmed.substring(1);
  return response;
}
```

## Format a string of names

- kyu: 6
- Given: an array containing hashes of names
- Return: a string formatted as a list of names separated by commas except for the last two names, which should be separated by an ampersand.

Examples

```javascript
list([{ name: "Bart" }, { name: "Lisa" }, { name: "Maggie" }]);
// returns 'Bart, Lisa & Maggie'

list([{ name: "Bart" }, { name: "Lisa" }]);
// returns 'Bart & Lisa'

list([{ name: "Bart" }]);
// returns 'Bart'

list([]);
// returns ''
```

My Solution:

```javascript
function list(names) {
  let temp = "";

  for (let i = 0; i < names.length; i++) {
    if (i == 0) {
      temp += names[i].name;
    } else if (i == names.length - 1) {
      temp += " & " + names[i].name;
    } else {
      temp += ", " + names[i].name;
    }
  }
  return temp;
}
```

## The highest profit wins

- kyu: 7

### Story

- Ben has a very simple idea to make some profit: he buys something and sells it again. Of course, this wouldn't give him any profit at all if he was simply to buy and sell it at the same price. Instead, he's going to buy it for the lowest possible price and sell it at the highest.

### Task

- a function that returns both the minimum and maximum number of the given list/array.

Examples

```javascript
minMax([1, 2, 3, 4, 5]) == [1, 5];
minMax([2334454, 5]) == [5, 2334454];
minMax([1]) == [1, 1];
```

My Solution:

```javascript
function minMax(arr) {
  let min = arr[0];
  let max = arr[0];
  arr.forEach((x) => {
    if (x > max) max = x;
    if (x < min) min = x;
  });
  return [min, max]; // fix me!
}
```

## Fake Binary

- kyu: 8
- Given: Given a string of digits, you should replace any digit below 5 with '0' and any digit 5 and above with '1'.
- Return: Return the resulting string.

My Solution:

```javascript
function fakeBin(x) {
  let temp = "";
  for (let i = 0; i < x.length; i++) {
    if (Number(x.substring(i, i + 1)) < 5) {
      temp += 0;
    } else {
      temp += 1;
    }
  }
  return temp;
}
```
