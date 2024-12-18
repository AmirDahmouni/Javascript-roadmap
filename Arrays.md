## Arrays

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

**iterating** over array items
```javascript
for (var i = 0; i < arr.length; i++)
arr.forEach(function (el, index) { ... })
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