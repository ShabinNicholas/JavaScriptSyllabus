# 16. Asynchronous JavaScript

`async`/`await` is modern syntax built on top of Promises (see [Promises](14-promises.md)) that lets asynchronous code **read like normal, top-to-bottom synchronous code** — no chains of `.then()`.

## `async`

Marking a function `async` means it always returns a Promise, and unlocks the ability to use `await` inside it.

```js
async function loadMessage() {
  return "Hello from an async function!";
}

loadMessage().then((msg) => console.log(msg));
// "Hello from an async function!"
```

## `await`

Pauses the function until a Promise settles, then gives you the resolved value directly — no `.then()` needed. `await` only works inside an `async` function.

```js
function fakeApiCall() {
  return new Promise((resolve) => {
    setTimeout(() => resolve("User data loaded"), 1000);
  });
}

async function getUser() {
  console.log("Fetching user...");
  const result = await fakeApiCall(); // pauses here until the promise resolves
  console.log(result);                // "User data loaded"
  console.log("Done!");
}

getUser();
// "Fetching user..."
// (waits 1 second)
// "User data loaded"
// "Done!"
```

## Error handling with `try`/`catch`

Since `await` unwraps a Promise's value, errors from a rejected promise are caught with a normal `try`/`catch` — same as [Error Handling](13-error-handling.md).

```js
function fakeApiCall(shouldFail) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      shouldFail ? reject("Network error") : resolve("Success!");
    }, 500);
  });
}

async function getData() {
  try {
    const result = await fakeApiCall(true);
    console.log(result);
  } catch (error) {
    console.log("Caught an error:", error);
  }
}

getData(); // "Caught an error: Network error"
```

## Running things in sequence vs. in parallel

```js
// Sequence — each await waits for the previous one to finish (slower)
async function sequential() {
  const a = await fakeApiCall(false); // waits ~500ms
  const b = await fakeApiCall(false); // then waits another ~500ms
}

// Parallel — start both at once, then wait for both together (faster)
async function parallel() {
  const [a, b] = await Promise.all([fakeApiCall(false), fakeApiCall(false)]);
}
```

## Try it yourself

```js
function fetchUser() {
  return new Promise((resolve) => setTimeout(() => resolve({ name: "Kai" }), 800));
}
function fetchPosts() {
  return new Promise((resolve) => setTimeout(() => resolve(["Post 1", "Post 2"]), 800));
}

// Write an async function `loadProfile` that fetches the user and posts
// in PARALLEL using Promise.all, then logs both results.
```

Next up: [17. Strings](17-strings.md) →
