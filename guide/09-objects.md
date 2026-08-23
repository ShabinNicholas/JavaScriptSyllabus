# 9. Objects

Building on the basics, this chapter covers the vocabulary and tools you'll use with objects every day.

## Object literals

The `{ key: value }` syntax itself is called an **object literal** — the most common way to create objects.

```js
const laptop = {
  brand: "Dell",
  ram: 16,
};
```

## Properties & methods

A **property** holds data. A **method** is a property whose value is a function.

```js
const dog = {
  name: "Rex",       // property
  bark() {           // method (shorthand syntax)
    return `${this.name} says woof!`;
  },
};

console.log(dog.bark()); // "Rex says woof!"
```

## Dot notation

```js
console.log(dog.name); // "Rex"
```

## Bracket notation

```js
console.log(dog["name"]); // "Rex"
```

## `this` keyword

Inside a method, `this` refers to "the object the method was called on." It lets an object refer to its own properties.

```js
const cat = {
  name: "Milo",
  greet() {
    console.log(`I'm ${this.name}!`); // this === cat here
  },
};

cat.greet(); // "I'm Milo!"
```

⚠️ Arrow functions don't get their own `this` — avoid arrow functions for object methods that need `this`.

## `Object.keys()`

Returns an array of an object's property names.

```js
const scores = { math: 90, science: 85, art: 70 };
console.log(Object.keys(scores)); // ["math", "science", "art"]
```

## `Object.values()`

Returns an array of an object's property values.

```js
console.log(Object.values(scores)); // [90, 85, 70]
```

## `Object.entries()`

Returns an array of `[key, value]` pairs — great for looping with `for...of`.

```js
console.log(Object.entries(scores));
// [["math", 90], ["science", 85], ["art", 70]]

for (const [subject, score] of Object.entries(scores)) {
  console.log(`${subject}: ${score}`);
}
```

## Object destructuring

A quick preview — its own full chapter is next.

```js
const { math, art } = scores;
console.log(math, art); // 90 70
```

## Try it yourself

```js
const inventory = { apples: 10, bananas: 5, cherries: 20 };
// Use Object.entries() and reduce() to calculate the total inventory count.
```

Next up: [10. Object Destructuring](10-object-destructuring.md) →
