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

JavaScript has typed values, not typed variables. The following built-in types are available:
```javascript
string
number
boolean
undefined // Something hasn't been initialised
null  // Something is currently unavailable
object
symbol (new to ES6) //Symbols in ES6 provide unique identifiers, avoiding property name collisions in objects.
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
**Callback hell** known as Pyramid of Doom occurs in JavaScript when multiple asynchronous operations are nested within one another using callbacks.
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

## ✅ Solutions to Avoid Callback Hell
1. Use Promises
```javascript
const fs = require("fs").promises;

fs.readFile("file1.txt", "utf8")
  .then((data1) => {
    console.log("File 1 content:", data1);
    return fs.readFile("file2.txt", "utf8");
  })
  .then((data2) => {
    console.log("File 2 content:", data2);
    return fs.readFile("file3.txt", "utf8");
  })
  .then((data3) => {
    console.log("File 3 content:", data3);
    console.log("All files have been read!");
  })
  .catch((err) => {
    console.error("Error reading files:", err);
  });
```

2. Use async/await
```javascript
const fs = require("fs").promises;

async function readFiles() {
  try {
    const data1 = await fs.readFile("file1.txt", "utf8");
    console.log("File 1 content:", data1);

    const data2 = await fs.readFile("file2.txt", "utf8");
    console.log("File 2 content:", data2);

    const data3 = await fs.readFile("file3.txt", "utf8");
    console.log("File 3 content:", data3);

    console.log("All files have been read!");
  } catch (err) {
    console.error("Error reading files:", err);
  }
}
readFiles();
```

3. Modularize Callbacks
```javascript
const fs = require("fs");

function readFile1(callback) {
  fs.readFile("file1.txt", "utf8", callback);
}

function readFile2(callback) {
  fs.readFile("file2.txt", "utf8", callback);
}

function readFile3(callback) {
  fs.readFile("file3.txt", "utf8", callback);
}

readFile1((err, data1) => {
  if (err) throw err;
  console.log("File 1 content:", data1);

  readFile2((err, data2) => {
    if (err) throw err;
    console.log("File 2 content:", data2);

    readFile3((err, data3) => {
      if (err) throw err;
      console.log("File 3 content:", data3);
      console.log("All files have been read!");
    });
  });
});
```

iterating over obeject proprities
```javascript
for (var property in obj) { console.log(property); }
Object.keys(obj).forEach(function (property) { ... })
```

iterating over array items
```javascript
for (var i = 0; i < arr.length; i++)
arr.forEach(function (el, index) { ... })
```

A **linear search** runs in at worst linear time and makes at most n comparisons, where n is the length of the list
```javascript
function linearSearch(array, toFind){
  for(let i = 0; i < array.length; i++){
    if(array[i] === toFind) return i;
  }
  return -1;
}
```

A **Binary search** find a target value in a sorted array by repeatedly dividing the search interval in half and comparing the target with the middle element.
```javascript
var binarySearch = function(array, value) {
    var guess,
        min = 0,
        max = array.length - 1;

    while(min <= max){
        guess = Math.floor((min + max) /2);
	if(array[guess] === value)
	    return guess;
	else if(array[guess] < value)
	    min = guess + 1;
	else
	    max = guess - 1;
     }
     return -1;
}
```
A generator is a function in JavaScript that can pause and resume its execution, producing multiple values using the yield keyword.
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


**Object.freeze()**: Prevents modifications to an object's properties
**const**: Declares a variable whose reference cannot be reassigned, but the value it holds can still be modified.

```javascript
const obj = { a: 1 };
Object.freeze(obj);
obj.a = 2; // This will not change the value of 'a'
console.log(obj.a); // 1

const obj = { a: 1 };
obj.a = 2; // This is allowed
obj = {};
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

Difference between **undefined** and **not defined**
```javascript
let x;
console.log(x); // undefined
console.log(y); // ReferenceError: y is not defined
```

Coercion in JavaScript is the automatic or implicit conversion of values from one type to another
```javascript
console.log('5' + 1); // "51" (string concatenation)
console.log('5' - 1); // 4 (string is coerced to a number)
```


**export default** is used to export a single value or entity from a module, making it the default export
```javascript
export default function add(a, b) {
  return a + b;
}

import add from './math';
console.log(add(2, 3)); // 5
```

Benefits of using **spread syntax**
```javascript
const arr1 = [1, 2];
const newArr = [...arr1]; // Copy of arr1

const arr2 = [3, 4];
const combined = [...newArr, ...arr2]; // [1, 2, 3, 4]

function sum(a, b, c) {
  return a + b + c;
}
onsole.log(sum(...combined));

const obj = { a: 1, b: 2 };
const newObj = { ...obj, b: 3 }; // { a: 1, b: 3 }
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