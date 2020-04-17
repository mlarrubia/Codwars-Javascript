## Challange 8

Name: Human readable duration format

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

  if (sec === 0) {
    return "now";
  }

  let obj = {
    year: Math.floor(sec / 31536000),
    day: Math.floor((sec % 31536000) / 86400),
    hour: Math.floor(((sec % 31536000) % 86400) / 3600),
    minute: Math.floor((((sec % 31536000) % 86400) % 3600) / 60),
    second: Math.floor((((sec % 31536000) % 86400) % 3600) % 60),
  };

  for (x in obj) {
    if (obj[x] >= 1) {
      count++;
    } else {
      delete obj[x];
    }
  }

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
    if (count == 1) {
      str += ` and `;
    }
  }
  return str;
}
```
