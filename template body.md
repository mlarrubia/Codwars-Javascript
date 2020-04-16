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
