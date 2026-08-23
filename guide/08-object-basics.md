# 8. Object Basics

Objects store data as **key-value pairs** — perfect for representing "a thing with properties" like a user, a product, or a car.

## Creating an object `{}`

```js
const person = {
  name: "Jordan",
  age: 32,
  isStudent: false,
};
```

## Creating an object with `new Object()`

Also rarely used in modern code, but good to recognize.

```js
const car = new Object();
car.brand = "Toyota";
car.year = 2022;
```

## Accessing properties (dot notation)

```js
console.log(person.name); // "Jordan"
```

## Accessing properties (bracket notation)

Required when the key is stored in a variable, or contains spaces/special characters.

```js
console.log(person["age"]); // 32

const key = "isStudent";
console.log(person[key]); // false — dot notation can't do this dynamic lookup
```

## Adding a new property

```js
person.email = "jordan@example.com";
console.log(person.email); // "jordan@example.com"
```

## Updating a property

```js
person.age = 33;
console.log(person.age); // 33
```

## Deleting a property

```js
delete person.isStudent;
console.log(person); // { name: "Jordan", age: 33, email: "jordan@example.com" }
```

## Looping with `for...in`

```js
for (const key in person) {
  console.log(`${key}: ${person[key]}`);
}
```

## Nested objects

Objects can contain other objects.

```js
const employee = {
  name: "Priya",
  address: {
    city: "Seattle",
    zip: "98101",
  },
};

console.log(employee.address.city); // "Seattle"
```

## Object inside an array

Combining the two is extremely common in real apps (API responses, database rows, etc.).

```js
const products = [
  { name: "Laptop", price: 999 },
  { name: "Mouse", price: 25 },
];

console.log(products[0].name); // "Laptop"
```

## Try it yourself

```js
// Create an object `book` with title, author, and pages.
// Add a `genre` property.
// Delete the `pages` property.
// Loop over the remaining properties with for...in and log "key: value" for each.
```

Next up: [9. Objects](09-objects.md) →
