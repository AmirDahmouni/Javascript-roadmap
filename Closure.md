## Closure

A **closure** occurs when a function "remembers" the variables from its lexical scope, even after the outer function has finished executing. this logic is used by react components
```javascript
function createCounter() {
  let count = 0;

  return function() {
    count++;
    console.log(count);
  };
}

const counter = createCounter();
counter(); // 1
counter(); // 2
```