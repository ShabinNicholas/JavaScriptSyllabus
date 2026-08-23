# 24. Classes (OOP)

Classes are templates for creating objects that share the same shape and behavior — the foundation of object-oriented programming in JavaScript. Under the hood, they're built on the same prototypes and closures you've already learned, just with friendlier syntax.

## `class` syntax

```js
class Animal {
  constructor(name, sound) {
    this.name = name;
    this.sound = sound;
  }

  makeSound() {
    console.log(`${this.name} says ${this.sound}`);
  }
}
```

## `constructor`

A special method that runs automatically when you create a new instance with `new`. It sets up the object's initial properties.

```js
const dog = new Animal("Rex", "Woof");
console.log(dog.name);  // "Rex"
console.log(dog.sound); // "Woof"
```

## Methods

Functions defined inside a class, shared by every instance (they live on the prototype, not copied onto each object — efficient even with thousands of instances).

```js
dog.makeSound(); // "Rex says Woof"

const cat = new Animal("Milo", "Meow");
cat.makeSound(); // "Milo says Meow"
```

## Inheritance (`extends`)

Lets one class build on another, reusing its properties and methods while adding or overriding its own.

```js
class Dog extends Animal {
  constructor(name, breed) {
    super(name, "Woof"); // call the parent constructor first
    this.breed = breed;
  }

  fetch() {
    console.log(`${this.name} fetches the ball!`);
  }
}

const rex = new Dog("Rex", "Labrador");
rex.makeSound(); // "Rex says Woof"  — inherited from Animal
rex.fetch();     // "Rex fetches the ball!" — defined on Dog
console.log(rex.breed); // "Labrador"
```

## `super` keyword

Calls the parent class's constructor or methods. **Must** be called before using `this` in a subclass constructor.

```js
class Puppy extends Dog {
  constructor(name, breed) {
    super(name, breed); // runs Dog's constructor (which runs Animal's constructor)
    this.isPuppy = true;
  }

  makeSound() {
    super.makeSound(); // call Animal's version first...
    console.log("...but with extra enthusiasm because puppy!");
  }
}

const buddy = new Puppy("Buddy", "Beagle");
buddy.makeSound();
// "Buddy says Woof"
// "...but with extra enthusiasm because puppy!"
```

## Try it yourself

```js
// Create a `Shape` class with a constructor that takes `name`,
// and a method `describe()` that logs "This is a {name}".
// Create a `Circle` class that extends Shape, adds a `radius`,
// and adds a method `area()` that returns Math.PI * radius ** 2.
```

Next up: [25. Node.js](25-nodejs.md) →
