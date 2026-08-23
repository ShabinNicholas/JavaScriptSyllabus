# 25. Node.js

Everything so far runs in a browser. **Node.js** lets you run JavaScript outside the browser — on a server, in a terminal, or as a script on your own machine. It's the same JavaScript language you already know, plus extra built-in tools browsers don't have (like file system access).

> This chapter is a brief on-ramp — a full Node.js syllabus is a course of its own, but these are the pieces that connect directly to what you've already learned.

## Running a script

```bash
node app.js
```

Any `.js` file becomes runnable from the terminal — no HTML page required.

```js
// app.js
console.log("Hello from Node.js!");
```

## The `console` and beyond

Everything from earlier chapters — variables, functions, arrays, classes, `async`/`await` — works identically in Node. What's different is the environment: there's no `window` or `document` (no DOM, see [chapter 12](12-dom-manipulation.md)), but there are new globals like `process` and modules like `fs`.

## CommonJS modules (`require` / `module.exports`)

Node traditionally uses its own module system, alongside the ES module `import`/`export` syntax from [chapter 21](21-modules.md).

```js
// mathUtils.js
function add(a, b) {
  return a + b;
}

module.exports = { add };
```

```js
// app.js
const { add } = require("./mathUtils");
console.log(add(2, 3)); // 5
```

## Reading files with the `fs` module

```js
const fs = require("fs");

// Synchronous — blocks until done, simplest for scripts:
const data = fs.readFileSync("notes.txt", "utf8");
console.log(data);

// Asynchronous — doesn't block, preferred for servers:
fs.readFile("notes.txt", "utf8", (error, data) => {
  if (error) {
    console.log("Error reading file:", error.message);
    return;
  }
  console.log(data);
});
```

## `npm` and `package.json`

`npm` (Node Package Manager) installs reusable libraries from the public registry, and `package.json` tracks your project's dependencies and metadata.

```bash
npm init -y          # create a package.json
npm install express  # install a library into node_modules/
```

```js
// package.json (created automatically)
{
  "name": "my-app",
  "version": "1.0.0",
  "dependencies": {
    "express": "^4.18.0"
  }
}
```

## A minimal web server

Node's built-in `http` module can serve web pages and APIs directly — no external library required.

```js
const http = require("http");

const server = http.createServer((request, response) => {
  response.writeHead(200, { "Content-Type": "text/plain" });
  response.end("Hello from a Node.js server!");
});

server.listen(3000, () => {
  console.log("Server running at http://localhost:3000");
});
```

Most real-world projects use a framework like **Express** on top of this for routing, middleware, and JSON handling — a natural next step once you're comfortable with the basics above.

## Try it yourself

```js
// Create a file `greet.js` that exports a function `greet(name)` using module.exports.
// Create `app.js` that requires it, calls greet("World"), and logs the result.
// Run it with: node app.js
```

← Back to [Home](/)
