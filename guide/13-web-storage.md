# 13. Web Storage

The browser can save data on the user's machine, so it's still there after a page refresh — no server required. There are two flavors: `localStorage` and `sessionStorage`. Both share the same methods; they only differ in how long the data sticks around.

## Local Storage

Data saved to `localStorage` persists **forever** — it survives page refreshes, tab closes, and even restarting the browser, until something explicitly clears it.

```js
localStorage.setItem("username", "Alex");

// Later, even after closing and reopening the browser:
console.log(localStorage.getItem("username")); // "Alex"
```

## Session Storage

Data saved to `sessionStorage` only lasts for the current **tab's session** — it's cleared as soon as that tab is closed. Each tab gets its own separate storage, even for the same site.

```js
sessionStorage.setItem("draft", "Unsaved note...");

// Available while this tab stays open, gone once it's closed.
console.log(sessionStorage.getItem("draft")); // "Unsaved note..."
```

## `setItem()`

Saves a key/value pair. Both the key and the value are stored as **strings** — if you need to store an object or array, convert it with `JSON.stringify()` first (see [chapter 24](24-working-with-data.md)).

```js
localStorage.setItem("theme", "dark");

const user = { name: "Alex", age: 30 };
localStorage.setItem("user", JSON.stringify(user));
```

## `getItem()`

Reads a value back by its key. Returns `null` if the key doesn't exist.

```js
console.log(localStorage.getItem("theme")); // "dark"
console.log(localStorage.getItem("missingKey")); // null

const user = JSON.parse(localStorage.getItem("user"));
console.log(user.name); // "Alex"
```

## `removeItem()`

Deletes a single key/value pair.

```js
localStorage.setItem("temp", "delete me");
localStorage.removeItem("temp");
console.log(localStorage.getItem("temp")); // null
```

## `clear()`

Wipes out **everything** stored under that storage object for the current site.

```js
localStorage.setItem("a", "1");
localStorage.setItem("b", "2");
localStorage.clear();
console.log(localStorage.getItem("a")); // null
```

## Try it yourself

```js
// Save a "visits" count to localStorage, starting at 0 if it doesn't exist yet.
// Each time this code runs, read the current count, add 1, and save it back.
// Log the updated count.
// Hint: localStorage always stores strings — convert with Number() when reading.
```

Next up: [14. Error Handling](14-error-handling.md) →
