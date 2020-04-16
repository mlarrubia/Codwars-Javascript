# Codwars Javascript

#### Kata: 6

| Name                                                | Kata | Tags                                                                        | Solution                   | Codewar Link                                                                                              |
| --------------------------------------------------- | ---- | --------------------------------------------------------------------------- | -------------------------- | --------------------------------------------------------------------------------------------------------- |
| Break the Caesar                                    | 5    | Fundamentals Ciphers Algorithms Cryptography Security Encryption Decryption | <[Solution](#challange-7)> | <[link](https://www.codewars.com/kata/598e045b8c13926d8c0000e8/train/python)>                             |
| Break camelCase                                     | 6    | Fundamentals Strings Formatting Algorithms                                  | <[Solution](#challange-6)> | <[link](https://www.codewars.com/kata/5208f99aee097e6552000148/train/javascript)>                         |
| array.Diff                                          | 6    | Fundamentals Arrays                                                         | <[Solution](#challange-5)> | <[link](https://www.codewars.com/kata/array-dot-diff)>                                                    |
| Title Case                                          | 6    | Fundamentals, Strings, Parsing, Algorithms                                  | [Solution](#challange-4)   | [link](https://www.codewars.com/kata/title-case)                                                          |
| Format a string of names like 'Bart, Lisa & Maggie' | 6    | Fundamentals, Strings, Formatting, Algorithms                               | [Solution](#challange-3)   | [link](https://www.codewars.com/kata/format-a-string-of-names-like-bart-lisa-and-maggie/train/javascript) |
| The highest profit wins!                            | 7    | Repetition, Decision, Arrays                                                | [Solution](#challange-2)   | [link](https://www.codewars.com/kata/the-highest-profit-wins/train/javascript)                            |
| Fake Binary                                         | 8    | Repetition, Decision, String Methods                                        | [Solution](#challange-1)   | [link](https://www.codewars.com/kata/fake-binary/train/javascript)                                        |

## Challange 7

Name: Break the Caesar!

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

def break_caesar(message):
  count = 0
  shift = 0
  for x in range(26):
    decryptedMessageRaw = decrypt(message, x)

    decryptedMessageFiltered = decryptedMessageRaw.translate(str.maketrans('', '', string.punctuation))

    arr = decryptedMessageFiltered.split(' ')
    current = checkCount(arr)
    if(current > count):
      count = current
      shift = x

  return shift



def checkCount(arr):
  num = 0
  for x in arr:
    word = x.lower()
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

## Challange 6

Name: Break camelCase

- kyu: 6
- Complete the solution so that the function will break up camel casing, using a space between words.

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

  b.forEach((num1) => {
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
  arr.forEach((x) => {
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
