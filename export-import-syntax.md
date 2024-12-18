**export default** is used to export a single value or entity from a module, making it the default export
```javascript
export default function add(a, b) {
  return a + b;
}

import add from './math';
console.log(add(2, 3)); // 5
```

The **import * as x from 'X'** syntax is used to import all exports from a module as a single object

```javascript
export const add = (a, b) => a + b;
export const subtract = (a, b) => a - b;

import * as math from './math';

console.log(math.add(2, 3)); // 5
console.log(math.subtract(5, 3)); // 2
```