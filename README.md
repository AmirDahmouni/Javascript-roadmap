# 🚀 JavaScript Roadmap

## 📦 Object Type

The **object** type refers to a compound value where you can set properties. Each property can hold its own value of any type.

```javascript
var obj = {
  a: "hello world",
  b: 42,
  c: true
};
```

JavaScript provides a **typeof** operator that can examine a value and tell you what type it is:
```javascript
typeof obj

a = 42;
typeof a;				// "number"
```

An array is an **object** that holds values (of any type) not particularly in named properties/keys
```javascript
const array = [
	"hello world",
	42,
	true
];

array[0];
array.length
typeof array
```
**Strict comparison** (e.g., ===) checks for value equality without allowing coercion

**Abstract comparison** (e.g. ==) checks for value equality with coercion allowed

## Global Scope, Function Scope, Block Scope & Lexical Scope

In JavaScript, **scope** determines where variables, functions, and objects are accessible in your code.
```javascript
var globalVar = "I am global";

function showGlobal() {

  var localVar = "I am local";
  let outerVar = "I'm from outer scope";
  console.log(globalVar); // Accessible here

  if (true) {
    let blockVar = "I exist only in this block";
    var functionVar = "I ignore block scope";
    console.log(blockVar); // Accessible here
  }

  console.log(blockVar); // Error: blockVar is not defined
  console.log(functionVar); // Accessible here (not block-scoped)
}

showGlobal();
console.log(globalVar); // Accessible here too
console.log(blockVar); // Error: blockVar is not defined
```

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


