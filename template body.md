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

<!-- This challenge wasn't to difficult. I rationalized this problem with a similar lab I did called
Mars Rover from Ironhack. Similarly I had to keep track of where I was on a 2D Grid. I remember
that I had an object that kept track of N, S, E, W so i applied the same logic. I did get stuck and
had to look for some help and found [Snail](https://www.youtube.com/watch?v=EWYrxOsBX58) that was perfect explaination to my positioning difficulties. Essentially, I created an object where I kept track of my row
& Col upper and Lower bounds to trace my path as a snail. Worked to perfection. -->
