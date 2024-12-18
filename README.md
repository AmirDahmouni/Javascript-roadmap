# 🚀 JavaScript Roadmap

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

**Hoisting** in JavaScript is the behavior where variable and function declarations are moved to the top of their containing scope during the compile phase, before the code is executed.


**Transpiling code** is the process of converting code written in one programming language or version of a language into another version or language, typically to make it compatible with different environments
Tools like **Babel** are commonly used for transpiling JavaScript code.
```javascript
// ES6+
const greet = () => {
  console.log('Hello');
};

// Transpiled to ES5
var greet = function() {
  console.log('Hello');
};
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

## iterating
iterating over obeject proprities
```javascript
for (var property in obj) { console.log(property); }
Object.keys(obj).forEach(function (property) { ... })

Object.values()
Object.entries()

const mapped = Object.entries(obj).map(([key, value]) => {
  return [key.toUpperCase(), value * 2];
});

```
iterating over array items
```javascript
for (var i = 0; i < arr.length; i++)
arr.forEach(function (el, index) { ... })
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

difference between function Person() var person= Person() and var person = new Preson()
```javascript
function Person() {
  this.name = 'John';
}
var person = Person(); // No 'new'
var person = new Person();  // Person { name: 'John' }
```

**Object Destructuring**: Unpacks properties based on the property names
```javascript
const person = { name: 'John', age: 30, city: 'New York' };

// Destructuring the object
const { name, age } = person;

console.log(name); // John
console.log(age);  // 30

```

**Array Destructuring**: Unpacks values based on their position in the array.
```javascript
const numbers = [10, 20, 30];

// Destructuring the array
const [first, second] = numbers;

console.log(first);  // 10
console.log(second); // 20
```


The key differences between **forEach** and **map** are Return Value,Modification of Original Array and Usage
```javascript
const arr = [1, 2, 3, 4];

// forEach (no return value)
arr.forEach(num => console.log(num * 2)); // Logs 2, 4, 6, 8

// map (returns a new array)
const doubled = arr.map(num => num * 2);
console.log(doubled); // [2, 4, 6, 8]

```



