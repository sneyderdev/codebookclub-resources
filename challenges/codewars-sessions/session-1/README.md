# CodeWars Sessions: Session #1
The challenge for this session was [Beginner Series #3 Sum of Numbers](https://www.codewars.com/kata/55f2b110f61eb01779000053/train/javascript).

## Solutions
```javascript
function getSum(a, b) {
  if (a === b) return a;
  else {
    let start = Math.min(a, b);
    let stop = Math.max(a, b);
    let step = 1;

    return Array(Math.ceil((stop - start + 1) / step)).fill(start).map((x, y) => x + y * step).reduce((total, num)=> total + num);
  }
}
```
---
```javascript
function getSum(a, b) {
  if (a === b) {
      return a;
  }

  let sum = 0;
  const minim = Math.min(a, b), maxim = Math.max(a, b);
  for (let i = minim; i <= maxim; i++) {
      sum += i;
  }

  return sum;
}
```
---
```javascript
function getSum(a, b) {
  if (a == b) {
      return a;
  } else {
      [lower, higher] = [a, b].sort();
      return 1 + getSum(lower, higher - 1);
  }
}
```
---
```javascript
function getSum(a, b) {
  if (a == b) {
    return a;
  }

  let lower = 0;
  let higher = 0;
  let suma = 0;

  if (a < b) {
    lower = a;
    higher = b;
  } else {
    lower = b;
    higher = a;
  }

  for (let i = lower; i <= higher; i++) {
    suma += i;
  }

  return suma;
}
```
---
```javascript
function getSum(a, b) {
  if(a === b) return a;

  let sorted = a < b ? [a, b] : [b, a];
  let diff = sorted[1] - sorted[0];

  return (sorted[0] + diff / 2) * (diff + 1);
}
```