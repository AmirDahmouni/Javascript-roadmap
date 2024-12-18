## Functions



A **generator** is a function in JavaScript that can pause and resume its execution, producing multiple values using the yield keyword.

**yield** is used in a generator function (function*), while **await** is used in an async function.
```javascript
function* generatorExample() {
  yield 1;
  yield 2;
  yield 3;
}
const gen = generatorExample();
console.log(gen.next().value); // 1
console.log(gen.next().value); // 2
console.log(gen.next().value); // 3

async function fetchData() {
  let result = await fetch('https://api.example.com/data');
  console.log(result);
}

```

**Extending built-in** JavaScript objects is generally not recommended as it can lead to unexpected behavior, conflicts, and reduce code readability.
```javascript
Array.prototype.last = function() {
  return this[this.length - 1];
};

const arr = [1, 2, 3];
console.log(arr.last()); // 3
```

**Arrow functions** provide a shorter syntax and preserve the this context from the surrounding scope.
```javascript
// Regular function
function regularFunction() {
  this.value = 1;
  setTimeout(function() {
    this.value++; // 'this' refers to the global object
    console.log(this.value); // NaN or undefined in strict mode
  }, 1000);
}

// Arrow function
function arrowFunction() {
  this.value = 1;
  setTimeout(() => {
    this.value++; // 'this' refers to the outer context
    console.log(this.value); // 2
  }, 1000);
}
```

An **anonymous function** is a function without a name, often used as a callback or passed as an argument to other functions.
```javascript
const sum = function(a, b) {
  return a + b;
};
console.log(sum(2, 3)); // 5

setTimeout(function() {
  console.log("Executed after 1 second");
}, 1000);
```

An **Immediately Invoked Function Expression** (IIFE) is a function that is defined and executed immediately after its creation.
```javascript
(function() {
  console.log('I am an IIFE');
})();
```

**Currying** is a technique in JavaScript where a function returns another function that takes arguments one by one
```javascript
function multiply(a) {
  return function(b) {
    return a * b;
  };
}
```

A **higher-order function** is a function that either takes one or more functions as arguments, returns a function, or both.
```javascript
// Function that takes another function as an argument
function add(a, b, callback) {
  return callback(a + b);
}

add(2, 3, function(result) {
  console.log(result); // 5
});
```
**Function.prototype.bind** creates a new function that, when called, has its this value set to the provided value and can optionally pre-fill arguments.

```javascript
const obj = { value: 42 };

function getValue() {
  return this.value;
}

const boundGetValue = getValue.bind(obj);
console.log(boundGetValue()); // 42
```

**.apply** and **.call** both are used to invoke a function with a specific this value, but the difference lies in how arguments are passed
```javascript
function greet(name, age) {
  console.log(`Hello, ${name}. You are ${age} years old.`);
}
greet.call(null, "Alice", 30);
greet.apply(null, ["Alice", 30]);
```