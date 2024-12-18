## Design patterns

**Singleton Pattern**: Ensures that a class has only one instance and provides a global point of access to that instance.
```javascript
class Singleton {
  constructor() {
    if (!Singleton.instance) {
      Singleton.instance = this;
    }
    return Singleton.instance;
  }
}

const instance1 = new Singleton();
const instance2 = new Singleton();
console.log(instance1 === instance2);
```

**Factory Pattern**: Provides an interface for creating objects, but allows subclasses to alter the type of objects that will be created.
```javascript
class Animal {
  speak() {
    console.log("Animal speaks");
  }
}

class Dog extends Animal {
  speak() {
    console.log("Woof");
  }
}

class Cat extends Animal {
  speak() {
    console.log("Meow");
  }
}

class AnimalFactory {
  static createAnimal(type) {
    if (type === 'dog') return new Dog();
    if (type === 'cat') return new Cat();
  }
}

const dog = AnimalFactory.createAnimal('dog');
dog.speak(); // Woof
```


**Observer Pattern**: Defines a one-to-many relationship where an object (subject) notifies its dependents (observers) of state changes
```javascript
class Subject {
  constructor() {
    this.observers = [];
  }

  addObserver(observer) {
    this.observers.push(observer);
  }

  notifyObservers() {
    this.observers.forEach(observer => observer.update());
  }
}

class Observer {
  update() {
    console.log("State changed!");
  }
}

const subject = new Subject();
const observer = new Observer();

subject.addObserver(observer);
subject.notifyObservers(); // State changed!

```


**Module Pattern**: Encapsulates code into a single object, providing privacy for variables and functions within a module.
```javascript
const CounterModule = (function() {
  let count = 0;

  return {
    increment: function() {
      count++;
      console.log(count);
    },
    decrement: function() {
      count--;
      console.log(count);
    }
  };
})();

CounterModule.increment(); // 1
CounterModule.increment(); // 2
CounterModule.decrement(); // 1
```


**Decorator Pattern**: Allows behavior to be added to an existing object dynamically.
```javascript
class Car {
  drive() {
    console.log("Driving");
  }
}

function electricDrive(car) {
  car.drive = function() {
    console.log("Driving electric car");
  };
}

const myCar = new Car();
electricDrive(myCar);
myCar.drive(); // Driving electric car
```
