# Codwars Javascript

| Name   |      Kata      |  Tags | Solution | Codewar Link |
|----------|-------------|------| -----| ----- |
| Fake Binary |  8 | Repetition, Decision, String Methods |[Solution](#challange-1) | [link](https://www.codewars.com/kata/fake-binary/train/javascript) |
| The highest profit wins! |  7 | Repetition, Decision, Arrays |[Solution](#challange-2) | [link](https://www.codewars.com/kata/the-highest-profit-wins/train/javascript) |



# Challange 1
Name: Fake Binary
- kyu: 8
- Given: Given a string of digits, you should replace any digit below 5 with '0' and any digit 5 and above with '1'.
- Return: Return the resulting string.

My Solution:
```javascript
function fakeBin(x){
let temp = '';
for(let i = 0; i < x.length; i++){
  if(Number(x.substring(i, i+1)) < 5){
    temp += 0;
  }
  else{
    temp += 1;
  }
}
 return temp;
}
```


# Challange 2
Name: The highest profit wins!
- kyu: 7
### Story
- Ben has a very simple idea to make some profit: he buys something and sells it again. Of course, this wouldn't give him any profit at all if he was simply to buy and sell it at the same price. Instead, he's going to buy it for the lowest possible price and sell it at the highest.

### Task
- a function that returns both the minimum and maximum number of the given list/array.

Examples
```javascript 
minMax([1,2,3,4,5])   == [1,5]
minMax([2334454,5])   == [5, 2334454]
minMax([1])           == [1, 1]
```

My Solution:
```javascript
function minMax(arr){
  let min = arr[0];
  let max = arr[0];
  arr.forEach((x) =>{
    if(x > max) max = x;
    if(x < min) min = x;
    });
  return [min, max]; // fix me!
}
```

