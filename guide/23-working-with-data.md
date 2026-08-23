# 23. Working with Data

Real apps need to send and receive data — usually as JSON — over the network. Here's the toolkit.

## `JSON.stringify()`

Converts a JavaScript object into a JSON **string** — needed when sending data over a network or saving it to a file.

```js
const user = { name: "Tara", age: 28, active: true };

const jsonString = JSON.stringify(user);
console.log(jsonString); // '{"name":"Tara","age":28,"active":true}'
console.log(typeof jsonString); // "string"

// Pretty-print with indentation (handy for logging/debugging):
console.log(JSON.stringify(user, null, 2));
```

## `JSON.parse()`

The reverse — converts a JSON string back into a real JavaScript object.

```js
const jsonString = '{"name":"Tara","age":28}';
const user = JSON.parse(jsonString);

console.log(user);      // { name: "Tara", age: 28 }
console.log(user.name); // "Tara" — it's a real object now, not a string
```

## `fetch()`

The modern, built-in way to make network requests. Returns a Promise (see [Promises](14-promises.md)).

```js
fetch("https://api.example.com/users/1")
  .then((response) => response.json()) // parse the JSON body — also returns a promise
  .then((data) => console.log(data))
  .catch((error) => console.log("Request failed:", error));
```

With `async`/`await` (see [chapter 15](15-asynchronous-javascript.md)) — the same request, easier to read:

```js
async function getUser(id) {
  try {
    const response = await fetch(`https://api.example.com/users/${id}`);
    const data = await response.json();
    console.log(data);
  } catch (error) {
    console.log("Request failed:", error);
  }
}
```

Sending data with `fetch` (a `POST` request):

```js
async function createUser(name) {
  const response = await fetch("https://api.example.com/users", {
    method: "POST",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify({ name }),
  });
  const data = await response.json();
  return data;
}
```

## AJAX / API calls

"AJAX" (Asynchronous JavaScript and XML — the name is a historical artifact; it's almost always JSON now) is the general term for a webpage fetching data **without reloading the page**. `fetch()` is the modern tool for it; you may also encounter the older `XMLHttpRequest` in legacy code, or libraries like `axios` that wrap `fetch`-like behavior with extra convenience.

```js
// The full picture: fetch -> check response -> parse JSON -> use the data
async function loadPosts() {
  const response = await fetch("https://api.example.com/posts");

  if (!response.ok) {
    throw new Error(`Request failed with status ${response.status}`);
  }

  const posts = await response.json();
  posts.forEach((post) => console.log(post.title));
}
```

## Try it yourself

```js
const localData = { id: 1, title: "Learn JS", done: false };
// Convert it to a JSON string and log it.
// Parse it back into an object and log the `title`.
// (If you have internet access) fetch "https://jsonplaceholder.typicode.com/todos/1"
// and log the response data.
```

Next up: [24. Classes (OOP)](24-classes-oop.md) →
