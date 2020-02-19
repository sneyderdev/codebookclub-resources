# CodeWars Sessions: Session #2
The challenge for this session was [Consecutive strings](https://www.codewars.com/kata/56a5d994ac971f1ac500003e/train/javascript).

## Solutions
```javascript
function longestConsec(strarr, k) {
  const n = strarr.length;
  if (n === 0 || k > n || k <= 0) {
    return "";
  }

  let result = "";
  for (let i = 0; i < n; i++) {
    let res='';
    for (let j = 0; j < k; j++) {
      if (i + j === n) break;
      res += strarr[i + j];
    }

    if (res.length > result.length) {
      result = res;
    }
  }

  return result;
}
```
---
```javascript
function longestConsec(strarr, k) {
  let n = strarr.length;
  if (n === 0 || k > n || k <= 0) return '';

  let output = '';
  let lengthArr = [];

  //get the lenght of all elements from strarr
  for (let i = 0; i < n; i++)
    lengthArr.push(strarr[i].length);

  //get the length of the current str length plus k consecutive ones
  for (let i = 0; i <= n - k; i++)
    for (let j = 1; j < k; j++)
      lengthArr[i] += lengthArr[i + j];

  // find the highest one
  let max = 0;
  for (let i = 0; i <= n - k; i++)
    if (lengthArr[i] > max) max = lengthArr[i];

  // concatenate with the output
  let maxIndex = lengthArr.indexOf(max);
  for (let i = maxIndex; i < maxIndex + k; i++)
    output += strarr[i];

  return output;
}
```
---
```javascript
function longestConsec(strarr, k) {
  const n = strarr.length;
  if (n === 0 || k > n || k <= 0) return "";

  let first = 0;
  let last = k;
  let longestString = strarr.slice(first, last).join('');

  for (let i = k; i < n; i++) {
    first = (i - k) + 1;
    last = i + 1;

    const newString = strarr.slice(first, last).join('');
    if (longestString.length < newString.length) {
      longestString = newString;
    }
  }

  return longestString;
}
```
---
```javascript
function longestConsec(strarr, k) {
  if (strarr.length === 0 || k > strarr.length || k <= 0 ) return '';

  let longestConsecutiveStrings = '';
  for (let i = 0; i <= strarr.length - k; i++) {
    const consecutiveStrings = strarr.slice(i, i + k).join('');
    longestConsecutiveStrings = longestConsecutiveStrings.length < consecutiveStrings.length ? consecutiveStrings : longestConsecutiveStrings;
  }

  return longestConsecutiveStrings;
}
```
---
```javascript
function longestConsecutive(aStrArr, iConsecStrings ) {
  // A minimum validation
  if ( aStrArr.length == 0 || aStrArr.length < iConsecStrings ) {
    return -1; // We return an error code
  }

  // Our first consecutive string is the longest so far
  // Saving the position is all we need
  let iLongestPos = 0;

  // We go through each of the rest consecutive strings and look into their lengths
  for ( let iPos = 1; iPos <= aStrArr.length - iConsecStrings; iPos++ ) {
    // If the current consecutive string is longer then, it is our new longest, we just ignore those with the same
    // length as the longest so far
    if (consecStrLength( aStrArr, iPos, iConsecStrings ) > consecStrLength( aStrArr, iLongestPos, iConsecStrings )) {
      iLongestPos = iPos;
    }
  }

  // We just return the position of the longest consecutive string
   return iLongestPos;
}
```