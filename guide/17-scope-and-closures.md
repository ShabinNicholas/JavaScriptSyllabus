# 17. Scope & Closures

Scope determines **where** a variable can be accessed. Understanding it prevents a huge class of confusing bugs.

## Global scope

Variables declared outside any function or block — accessible from anywhere in the file.

```js
const appName = "MyApp"; // global

function showName() {
  console.log(appName); // accessible here too
}
```

## Local scope

Variables declared inside a function only exist inside that function.

```js
function greet() {
  const message = "Hi there"; // local to greet()
  console.log(message);
}

greet();
// console.log(message); // ❌ ReferenceError — not accessible out here
```

## Block scope

`let` and `const` are scoped to the nearest `{ }` block (an `if`, a `for`, etc.) — not just the nearest function. `var` ignores block scope entirely, which is a major reason to avoid it.

```js
if (true) {
  let blockScoped = "only visible in here";
  var notBlockScoped = "leaks out of the block";
}

// console.log(blockScoped);   // ❌ ReferenceError
console.log(notBlockScoped);   // ✅ "leaks out of the block" — var ignores the block
```

## Hoisting

JavaScript moves function and variable **declarations** to the top of their scope before running the code. `var` declarations are hoisted and initialized as `undefined`; `let`/`const` are hoisted but stay uninitialized (the "temporal dead zone") until their line runs.

```js
console.log(hoistedVar); // undefined — declaration is hoisted, value is not
var hoistedVar = "I'm declared with var";

// console.log(hoistedLet); // ❌ ReferenceError: Cannot access before initialization
let hoistedLet = "I'm declared with let";
```

Function declarations are fully hoisted, body and all — that's why you can call them before they appear in the file:

```js
sayHi(); // ✅ works fine

function sayHi() {
  console.log("Hi!");
}
```

## Closures

A closure is a function that "remembers" the variables from the scope it was created in, even after that outer scope has finished running. This is one of JavaScript's most powerful — and most asked-about-in-interviews — features.

```js
function makeCounter() {
  let count = 0; // this variable is "enclosed" by the inner function

  return function () {
    count++;
    return count;
  };
}

const counter = makeCounter();
console.log(counter()); // 1
console.log(counter()); // 2
console.log(counter()); // 3
// `count` persists between calls because the returned function
// keeps a private reference to it — no other code can touch `count` directly.
```

Closures are how you build private state in JavaScript, and they power patterns you've already seen, like the higher-order `multiplyBy` example in [Functions](05-functions.md).

## Try it yourself

```js
// Write a function `createBankAccount(startingBalance)` that returns an object
// with `deposit(amount)` and `getBalance()` methods, using a closure to
// keep the balance private (not accessible directly from outside).
```

Next up: [18. ES6+ Features](18-es6-features.md) →
