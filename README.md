# Codwars Javascript

| Name   |      Kata      |  Tags | Link |
|----------|-------------|------| -----|
| Fake Binary |  8 | Repetition, Decision, String Methods | [link](https://www.codewars.com/kata/fake-binary/train/javascript) |



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
