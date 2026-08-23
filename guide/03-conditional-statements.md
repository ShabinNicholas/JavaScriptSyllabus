# 3. Conditional Statements

Conditionals let your code make decisions and run different code depending on the situation.

## `if` statement

```js
const temperature = 30;

if (temperature > 25) {
  console.log("It's hot outside!");
}
```

## `if...else` statement

```js
const isRaining = true;

if (isRaining) {
  console.log("Bring an umbrella.");
} else {
  console.log("Enjoy the sunshine!");
}
```

## `else if` statement

Chain multiple conditions in order — the first one that's `true` wins.

```js
const score = 72;

if (score >= 90) {
  console.log("Grade: A");
} else if (score >= 80) {
  console.log("Grade: B");
} else if (score >= 70) {
  console.log("Grade: C");
} else {
  console.log("Grade: F");
}
// Logs "Grade: C"
```

## Nested `if` statement

An `if` inside another `if`, for when a decision depends on more than one thing.

```js
const isMember = true;
const cartTotal = 120;

if (isMember) {
  if (cartTotal > 100) {
    console.log("You get free shipping AND a member discount!");
  } else {
    console.log("You get a member discount.");
  }
} else {
  console.log("Join to unlock discounts.");
}
```

## `switch` statement

A cleaner alternative to a long `if...else if` chain when you're comparing one value against many exact options.

```js
const day = "Tuesday";

switch (day) {
  case "Monday":
    console.log("Start of the work week.");
    break;
  case "Tuesday":
  case "Wednesday":
  case "Thursday":
    console.log("Midweek grind.");
    break;
  case "Friday":
    console.log("Almost there!");
    break;
  default:
    console.log("It's the weekend!");
}
// Logs "Midweek grind."
```

Don't forget `break` — without it, execution "falls through" into the next case.

## Try it yourself

```js
// Write a function that takes a `weather` string ("sunny", "rainy", "snowy")
// and uses a switch statement to log an appropriate outfit suggestion.
```

Next up: [4. Loops](04-loops.md) →
