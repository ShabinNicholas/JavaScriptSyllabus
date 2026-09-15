# 14. Error Handling

Things go wrong — bad input, failed network requests, typos in code. Error handling lets your program fail gracefully instead of crashing.

## `try`

Wrap risky code in a `try` block. If something inside throws an error, execution jumps straight to `catch`.

```js
try {
  const result = JSON.parse("this is not valid JSON");
  console.log(result); // never runs — parsing fails first
} catch (error) {
  console.log("Something went wrong!");
}
```

## `catch`

Runs only if the `try` block threw an error. The error object tells you what happened.

```js
try {
  const data = JSON.parse("{ invalid }");
} catch (error) {
  console.log("Error message:", error.message);
  console.log("Error name:", error.name); // e.g. "SyntaxError"
}
```

## `finally`

Runs **no matter what** — whether the `try` succeeded or the `catch` caught an error. Great for cleanup (closing a connection, hiding a loading spinner).

```js
function loadData() {
  try {
    console.log("Loading...");
    throw new Error("Network failed");
  } catch (error) {
    console.log("Caught:", error.message);
  } finally {
    console.log("Done loading (success or fail).");
  }
}

loadData();
// "Loading..."
// "Caught: Network failed"
// "Done loading (success or fail)."
```

## `throw` statement

Lets **you** create and raise your own errors, for situations your code decides are invalid.

```js
function withdraw(balance, amount) {
  if (amount > balance) {
    throw new Error("Insufficient funds");
  }
  return balance - amount;
}

try {
  withdraw(100, 500);
} catch (error) {
  console.log(error.message); // "Insufficient funds"
}
```

You can throw any value, but throwing an `Error` object (or a subclass of it) is best practice — it comes with a useful `message`, `name`, and stack trace.

## Try it yourself

```js
function divide(a, b) {
  // Throw an error if b is 0 ("Cannot divide by zero").
  // Otherwise return a / b.
}

// Call divide(10, 0) inside a try/catch and log a friendly error message.
// Call divide(10, 2) inside the same try/catch and log the result.
```

Next up: [15. Promises](15-promises.md) →
