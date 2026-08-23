# 10. Object Destructuring

Destructuring lets you unpack values from an object (or array) into their own variables, without repeating the object name over and over.

## Basic object destructuring

```js
const user = { name: "Lena", age: 27, country: "Canada" };

// The old way:
const name1 = user.name;
const age1 = user.age;

// The destructured way — same result, much shorter:
const { name, age, country } = user;

console.log(name, age, country); // "Lena" 27 "Canada"
```

## Destructuring with renaming

Use a colon to give the extracted variable a different local name.

```js
const { name: userName, age: userAge } = user;
console.log(userName); // "Lena"
console.log(userAge);  // 27
```

## Destructuring with default values

Provide a fallback for when the property doesn't exist.

```js
const { name, nickname = "N/A" } = user;
console.log(nickname); // "N/A" — user has no nickname property
```

Combine renaming and defaults together:

```js
const { country: location = "Unknown" } = user;
console.log(location); // "Canada"
```

## Nested object destructuring

Pull values out of objects inside objects in one step.

```js
const profile = {
  username: "lena92",
  contact: {
    email: "lena@example.com",
    phone: "555-1234",
  },
};

const {
  contact: { email, phone },
} = profile;

console.log(email); // "lena@example.com"
console.log(phone); // "555-1234"
```

## Destructuring function parameters

Extremely common in real-world code — destructure right in the function signature.

```js
function printUser({ name, age }) {
  console.log(`${name} is ${age} years old.`);
}

printUser(user); // "Lena is 27 years old."

// With defaults, for optional fields:
function greet({ name, greeting = "Hello" } = {}) {
  console.log(`${greeting}, ${name}!`);
}

greet({ name: "Sam" }); // "Hello, Sam!"
```

## Try it yourself

```js
const movie = {
  title: "Inception",
  year: 2010,
  director: { name: "Christopher Nolan", country: "UK" },
};
// Destructure title and year directly.
// Destructure the director's name, renaming it to `directorName`.
// Write a function `printMovie` that takes a movie object and destructures it in the parameter list.
```

Next up: [11. Events](11-events.md) →
