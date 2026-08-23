# 4. Loops

Loops repeat a block of code so you don't have to copy-paste it over and over.

## `for` loop

Best when you know how many times you want to repeat something.

```js
for (let i = 0; i < 5; i++) {
  console.log(`Iteration number ${i}`);
}
// 0, 1, 2, 3, 4
```

- `let i = 0` — starting point
- `i < 5` — keep going while this is true
- `i++` — what to do after each round

## `while` loop

Best when you don't know in advance how many times you'll loop — you just know the stopping condition.

```js
let energy = 3;

while (energy > 0) {
  console.log(`Energy left: ${energy}`);
  energy--;
}
```

## `do...while` loop

Like `while`, but always runs **at least once**, because the condition is checked at the end.

```js
let attempts = 0;

do {
  console.log("Trying to connect...");
  attempts++;
} while (attempts < 1 && false);
// Runs once even though the condition is false
```

## `for...in` loop

Loops over the **keys** of an object (or indexes of an array — but prefer `for...of` for arrays).

```js
const user = { name: "Sam", age: 28, city: "Austin" };

for (const key in user) {
  console.log(`${key}: ${user[key]}`);
}
// name: Sam
// age: 28
// city: Austin
```

## `for...of` loop

Loops over the **values** of an iterable (arrays, strings, Maps, Sets). This is usually what you want for arrays.

```js
const fruits = ["apple", "banana", "cherry"];

for (const fruit of fruits) {
  console.log(fruit);
}
// apple
// banana
// cherry
```

## `break` statement

Immediately exits the loop.

```js
for (let i = 0; i < 10; i++) {
  if (i === 3) break;
  console.log(i);
}
// 0, 1, 2  (stops before printing 3)
```

## `continue` statement

Skips just this iteration and moves to the next one.

```js
for (let i = 0; i < 5; i++) {
  if (i === 2) continue;
  console.log(i);
}
// 0, 1, 3, 4  (2 is skipped)
```

## Nested loops

A loop inside another loop — useful for grids, tables, and combinations.

```js
for (let row = 1; row <= 3; row++) {
  for (let col = 1; col <= 3; col++) {
    console.log(`Row ${row}, Col ${col}`);
  }
}
// 9 total lines: every combination of row 1-3 and col 1-3
```

## Try it yourself

```js
// Use a for loop to print the first 10 even numbers.
// Then use for...of to loop over ["red", "green", "blue"] and log each one uppercase.
```

Next up: [5. Functions](05-functions.md) →
