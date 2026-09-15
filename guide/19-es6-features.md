# 19. ES6+ Features

"ES6" (ECMAScript 2015) introduced a wave of syntax that makes JavaScript much nicer to write. Here are three you'll use constantly.

## Array destructuring

Like object destructuring (see [chapter 10](10-object-destructuring.md)), but for arrays — position matters instead of key names.

```js
const colors = ["red", "green", "blue"];

const [first, second, third] = colors;
console.log(first, second, third); // "red" "green" "blue"

// Skip items with a blank spot:
const [, , onlyThird] = colors;
console.log(onlyThird); // "blue"

// Swap two variables in one line — a classic destructuring trick:
let a = 1;
let b = 2;
[a, b] = [b, a];
console.log(a, b); // 2 1
```

## Spread operator (`...`)

"Expands" an array or object into individual elements — for copying, merging, or passing as arguments.

```js
// Copying an array (a new array, not a reference to the old one):
const original = [1, 2, 3];
const copy = [...original, 4, 5];
console.log(copy); // [1, 2, 3, 4, 5]

// Merging arrays:
const merged = [...[1, 2], ...[3, 4]];
console.log(merged); // [1, 2, 3, 4]

// Copying/merging objects:
const base = { name: "Kai", role: "user" };
const admin = { ...base, role: "admin" }; // override role, keep the rest
console.log(admin); // { name: "Kai", role: "admin" }

// Spreading into function arguments:
function sum(a, b, c) {
  return a + b + c;
}
const nums = [1, 2, 3];
console.log(sum(...nums)); // 6
```

## Rest parameters

The opposite idea, used in a function signature — "gather up" any remaining arguments into a real array. Looks identical (`...`) but behaves oppositely depending on where it's used.

```js
function sumAll(...numbers) {
  // `numbers` is a real array, no matter how many arguments are passed
  return numbers.reduce((total, n) => total + n, 0);
}

console.log(sumAll(1, 2, 3));       // 6
console.log(sumAll(1, 2, 3, 4, 5)); // 15

// Rest can follow named parameters too:
function introduce(name, ...hobbies) {
  console.log(`${name}'s hobbies: ${hobbies.join(", ")}`);
}

introduce("Mia", "reading", "hiking", "chess");
// "Mia's hobbies: reading, hiking, chess"
```

## Try it yourself

```js
// Use array destructuring to swap the first and last elements of [10, 20, 30, 40].
// Use the spread operator to combine { a: 1 } and { b: 2 } into one object.
// Write a function `logAll(...args)` that logs every argument passed to it.
```

Next up: [20. Timers](20-timers.md) →
