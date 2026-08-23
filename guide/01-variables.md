# 1. Variables

Variables are labeled boxes that hold data so you can reuse and change it later. JavaScript gives you three ways to create one, and a handful of built-in data types to store inside them.

## `var`, `let`, and `const`

```js
var oldWay = "works, but avoid it";   // function-scoped, can be redeclared — a common source of bugs
let score = 10;                       // block-scoped, can be reassigned
const name = "Ava";                   // block-scoped, CANNOT be reassigned

score = 20;        // ✅ fine, let allows reassignment
// name = "Zoe";   // ❌ TypeError: Assignment to constant variable.
```

**Rule of thumb:** reach for `const` by default. Use `let` only when you know the value will change. Avoid `var` in modern code — it doesn't respect block scope (see [Scope & Closures](17-scope-and-closures.md)).

## String data type

Text, wrapped in quotes.

```js
const greeting = "Hello";
const singleQuotes = 'also fine';
const template = `Hi, my name is ${greeting}`; // template literals — see Strings chapter
```

## Number data type

JavaScript has just one number type — no separate "integer" vs "float".

```js
const age = 25;
const price = 19.99;
const negative = -4;
```

## Boolean data type

Only two possible values: `true` or `false`. Used for yes/no, on/off decisions.

```js
const isLoggedIn = true;
const hasPermission = false;
```

## Undefined & Null

Both mean "no value", but for different reasons:

```js
let notYetSet;
console.log(notYetSet); // undefined — declared, but never given a value

const empty = null;     // deliberately set to "nothing" by you, the developer
```

Think of it this way: `undefined` means "JavaScript hasn't set this yet." `null` means "a human decided this is empty on purpose."

## `typeof` operator

Tells you what kind of value you're dealing with — handy for debugging.

```js
typeof "hello";     // "string"
typeof 42;           // "number"
typeof true;         // "boolean"
typeof undefined;    // "undefined"
typeof null;         // "object"  <- a famous, long-standing JS quirk!
typeof [1, 2, 3];    // "object"  (arrays are objects too)
```

## Try it yourself

```js
// Declare a const called `favoriteFood` with your favorite food as a string.
// Declare a let called `slicesEaten` starting at 0.
// Log the typeof each variable.
// Then reassign `slicesEaten` to 3 and log it again.
```

Next up: [2. Operators](02-operators.md) →
