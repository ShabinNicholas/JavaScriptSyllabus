# 15. Promises

A **Promise** represents a value that isn't ready yet, but will be — eventually — either successfully (**resolved**) or unsuccessfully (**rejected**). They're JavaScript's answer to "how do I handle something that takes time?" (like a network request).

## Promise object

```js
const myPromise = new Promise((resolve, reject) => {
  const success = true;

  setTimeout(() => {
    if (success) {
      resolve("Data loaded!"); // fulfilled
    } else {
      reject("Something went wrong."); // rejected
    }
  }, 1000);
});
```

A promise is always in one of three states: **pending** (not done yet), **fulfilled** (succeeded), or **rejected** (failed).

## `.then()`

Runs when the promise resolves successfully. Receives the resolved value.

```js
myPromise.then((result) => {
  console.log(result); // "Data loaded!" (after 1 second)
});
```

## `.catch()`

Runs when the promise is rejected. Always add one — an unhandled rejection can crash a Node process or silently fail in the browser.

```js
myPromise
  .then((result) => console.log(result))
  .catch((error) => console.log("Error:", error));
```

## `.finally()`

Runs after the promise settles, whether it succeeded or failed — great for cleanup like hiding a spinner.

```js
myPromise
  .then((result) => console.log(result))
  .catch((error) => console.log("Error:", error))
  .finally(() => console.log("Request finished."));
```

## `Promise.all()`

Waits for **every** promise in a list to resolve, then gives you all the results together. If any single one rejects, the whole thing rejects immediately.

```js
const p1 = Promise.resolve(10);
const p2 = Promise.resolve(20);
const p3 = new Promise((resolve) => setTimeout(() => resolve(30), 500));

Promise.all([p1, p2, p3]).then((results) => {
  console.log(results); // [10, 20, 30] — after ~500ms, once the slowest one finishes
});
```

Useful when you need to fire off several independent requests (e.g. loading a user's profile, posts, and settings at once) and wait for all of them before continuing.

## Try it yourself

```js
function fakeApiCall(shouldSucceed) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      if (shouldSucceed) resolve("Success!");
      else reject("Failed!");
    }, 500);
  });
}

// Call fakeApiCall(true), log the result with .then(), and add a .catch() too.
// Then try fakeApiCall(false) and confirm .catch() runs instead.
```

Next up: [16. Asynchronous JavaScript](16-asynchronous-javascript.md) →
