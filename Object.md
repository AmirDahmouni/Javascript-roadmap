## Object Type

The **object** type refers to a compound value where you can set properties. Each property can hold its own value of any type.

```javascript
var obj = {
  a: "hello world",
  b: 42,
  c: true
};
```
**iterating** over obeject proprities
```javascript
for (var property in obj) { console.log(property); }
Object.keys(obj).forEach(function (property) { ... })

Object.values()
Object.entries()

const mapped = Object.entries(obj).map(([key, value]) => {
  return [key.toUpperCase(), value * 2];
});
```

**Object Destructuring**: Unpacks properties based on the property names
```javascript
const person = { name: 'John', age: 30, city: 'New York' };

// Destructuring the object
const { name, age } = person;

console.log(name); // John
console.log(age);  // 30

```

**Strict comparison** (e.g., ===) checks for value equality without allowing coercion

**Abstract comparison** (e.g. ==) checks for value equality with coercion allowed
```javascript
var err1 = Error('message');
var err2 = new Error('message');
console.log(err1 === err2) // true
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


The primary **drawback** of true private variables in JavaScript (using methods like closures or # in class fields)
The **new** keyword in JavaScript is used to create an instance of an object
```javascript
class MyClass {
  #privateVar;

  constructor(value) {
    this.#privateVar = value;
  }

  getPrivateVar() {
    return this.#privateVar;
  }
}

const obj = new MyClass(10);
console.log(obj.getPrivateVar()); // 10
console.log(obj.#privateVar); // SyntaxError: Private field '#privateVar' must be declared in an enclosing class
```