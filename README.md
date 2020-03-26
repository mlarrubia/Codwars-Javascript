# Codwars Javascript

#### Kata: 6

| Name                                                | Kata | Tags                                          | Solution                   | Codewar Link                                                                                              |
| --------------------------------------------------- | ---- | --------------------------------------------- | -------------------------- | --------------------------------------------------------------------------------------------------------- |
| array.Diff                                          | 6    | Fundamentals Arrays                           | <[Solution](#challange-5)> | <[link](https://www.codewars.com/kata/array-dot-diff)>                                                    |
| Title Case                                          | 6    | Fundamentals, Strings, Parsing, Algorithms    | [Solution](#challange-4)   | [link](https://www.codewars.com/kata/title-case)                                                          |
| Format a string of names like 'Bart, Lisa & Maggie' | 6    | Fundamentals, Strings, Formatting, Algorithms | [Solution](#challange-3)   | [link](https://www.codewars.com/kata/format-a-string-of-names-like-bart-lisa-and-maggie/train/javascript) |
| The highest profit wins!                            | 7    | Repetition, Decision, Arrays                  | [Solution](#challange-2)   | [link](https://www.codewars.com/kata/the-highest-profit-wins/train/javascript)                            |
| Fake Binary                                         | 8    | Repetition, Decision, String Methods          | [Solution](#challange-1)   | [link](https://www.codewars.com/kata/fake-binary/train/javascript)                                        |

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

## Challange 4

Name: Title Case

- kyu: 6
- Write a function that will convert a string into title case, given an optional list of exceptions (minor words). The list of minor words will be given as a string with each word separated by a space. Your function should ignore the case of the minor words string -- it should behave in the same way even if the case of the minor word string is changed.

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
  titleArray.forEach(word => {
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

## Challange 3

Name: Format a string of names like 'Bart, Lisa & Maggie'.

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

## Challange 2

Name: The highest profit wins!

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
  arr.forEach(x => {
    if (x > max) max = x;
    if (x < min) min = x;
  });
  return [min, max]; // fix me!
}
```

## Challange 1

Name: Fake Binary

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
