# 21. Modules

Modules let you split code across multiple files, each exposing only what it wants to share. This keeps large projects organized and avoids polluting the global scope.

## `export` statement

Marks something inside a file as available to other files.

```js
// mathUtils.js
export const PI = 3.14159;

export function add(a, b) {
  return a + b;
}

export function subtract(a, b) {
  return a - b;
}
```

## `import` statement

Pulls exported values into another file.

```js
// app.js
import { PI, add, subtract } from "./mathUtils.js";

console.log(add(2, 3));      // 5
console.log(subtract(5, 2)); // 3
console.log(PI);             // 3.14159
```

You can rename things on import too:

```js
import { add as addNumbers } from "./mathUtils.js";
console.log(addNumbers(1, 1)); // 2
```

Or import everything under one namespace object:

```js
import * as MathUtils from "./mathUtils.js";
console.log(MathUtils.add(2, 2)); // 4
```

## Default export vs named export

A file can have **one** default export (imported without curly braces, and you can name it anything on import), plus **any number** of named exports (imported with curly braces, using their exact names).

```js
// user.js
export default function createUser(name) {
  return { name };
}

export const ROLE_ADMIN = "admin";
export const ROLE_GUEST = "guest";
```

```js
// app.js
import createUser, { ROLE_ADMIN, ROLE_GUEST } from "./user.js";

const user = createUser("Priya");
console.log(user);       // { name: "Priya" }
console.log(ROLE_ADMIN); // "admin"
```

**Rule of thumb:** use a default export when a file represents one main "thing" (like a single component or class). Use named exports for utility files with multiple related helpers.

> To use `import`/`export` in the browser, load your script with `<script type="module" src="app.js"></script>`. In Node.js, either use the `.mjs` extension or set `"type": "module"` in your `package.json`.

## Try it yourself

```js
// Create a file `stringUtils.js` with named exports `capitalize` and `reverse`.
// Create a file `main.js` that imports both and uses them on a sample string.
```

Next up: [22. Dates](22-dates.md) →
