# 5. Functions

Functions are reusable blocks of code you can run whenever you need them — the backbone of organized JavaScript.

## Function declaration

```js
function greet(name) {
  return `Hello, ${name}!`;
}

console.log(greet("Maya")); // "Hello, Maya!"
```

Function declarations are **hoisted** — you can call them before they appear in the file (see [Scope & Closures](17-scope-and-closures.md)).

## Function expression

A function stored in a variable. Not hoisted the same way — it only exists once the line runs.

```js
const greet = function (name) {
  return `Hello, ${name}!`;
};
```

## Arrow function

A shorter syntax, very common in modern JS. Also handles `this` differently (it doesn't get its own `this`).

```js
const greet = (name) => {
  return `Hello, ${name}!`;
};

// If the function body is just one return statement, shorten it further:
const greetShort = (name) => `Hello, ${name}!`;

// Single parameter? Parentheses are optional:
const double = n => n * 2;
```

## Parameters

The named placeholders a function expects when called.

```js
function add(a, b) {
  return a + b;
}
```

## Arguments

The actual values you pass in when calling the function.

```js
add(3, 4); // 3 and 4 are the arguments
```

## Default parameters

Fallback values used when an argument isn't provided.

```js
function greet(name = "friend") {
  return `Hello, ${name}!`;
}

console.log(greet());        // "Hello, friend!"
console.log(greet("Priya")); // "Hello, Priya!"
```

## Return statement

Sends a value back to wherever the function was called. Without `return`, a function gives back `undefined`.

```js
function square(n) {
  return n * n; // stops the function here and hands back the value
  // any code after this line never runs
}
```

## Callback function

A function passed into another function, to be run later.

```js
function processOrder(callback) {
  console.log("Order placed.");
  callback(); // run whatever function was passed in
}

processOrder(function () {
  console.log("Order confirmed!");
});
```

## Anonymous function

A function with no name — usually passed directly as an argument.

```js
setTimeout(function () {
  console.log("This function has no name.");
}, 1000);
```

## Function scope

Variables declared inside a function only exist inside that function.

```js
function example() {
  const secret = "only visible in here";
  console.log(secret);
}

example();
// console.log(secret); // ❌ ReferenceError: secret is not defined
```

## Recursion

A function that calls itself, useful for problems that break down into smaller versions of themselves.

```js
function factorial(n) {
  if (n <= 1) return 1;      // base case — stops the recursion
  return n * factorial(n - 1); // recursive case — calls itself with a smaller n
}

console.log(factorial(5)); // 120  (5 * 4 * 3 * 2 * 1)
```

Every recursive function needs a **base case**, or it will call itself forever.

## Higher-order functions

A function that takes another function as an argument, or returns a function. Array methods like `map` and `filter` are the most common examples (see [Array Methods](07-array-methods.md)).

```js
function multiplyBy(factor) {
  return function (n) {
    return n * factor;
  };
}

const triple = multiplyBy(3);
console.log(triple(10)); // 30
```

## Try it yourself

```js
// Write an arrow function `isEven` that returns true/false for a given number.
// Write a higher-order function `repeat(fn, times)` that calls `fn` that many times.
```

Next up: [6. Array Basics](06-array-basics.md) →
