# 🚀 JavaScript Roadmap

## Object Type

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
```javascript
var err1 = Error('message');
var err2 = new Error('message');
console.log(err1 === err2) // true
```

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

## Host objects & Native Objects

Native objects are objects that are part of the JavaScript language, such as String, Math, RegExp, Object, Function, etc.

Host objects are provided by the runtime environment, such as window, NodeList, console

## What is origin policy
The same-origin policy prevents JavaScript from making requests across domain boundaries. An origin is defined as a combination of URI scheme, hostname, and port number

## Strict Mode
In Node.js (and JavaScript in general), strict mode is a feature that enforces a stricter set of rules for JavaScript code.
Modules in Node.js automatically run in strict mode
```javascript
"use strict";
let public = 1; // Error: Unexpected strict mode reserved word

var myVar = 10;
delete myVar; // Error: Cannot delete 'myVar'

x = 3.14; // Error: 'x' is not defined
console.log(x);

function myFunction() {
  "use strict";
  y = 3.14; // Error: 'y' is not defined
}
```

## Callback Hell
Callback hell known as Pyramid of Doom occurs in JavaScript when multiple asynchronous operations are nested within one another using callbacks.
```javascript
fs.readFile("file1.txt", "utf8", (err, data1) => {
  if (err) throw err;
  console.log("File 1 content:", data1);

  fs.readFile("file2.txt", "utf8", (err, data2) => {
    if (err) throw err;
    console.log("File 2 content:", data2);

    fs.readFile("file3.txt", "utf8", (err, data3) => {
      if (err) throw err;
      console.log("File 3 content:", data3);

      console.log("All files have been read!");
    });
  });
});
```




