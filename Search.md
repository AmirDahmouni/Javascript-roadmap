## Search
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