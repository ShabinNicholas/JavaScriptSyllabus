# 17. Strings

Strings come with plenty of built-in methods for reading and transforming text.

> Sample string used throughout this page:
> ```js
> const text = "  Hello, World!  ";
> ```

## `toUpperCase()`

```js
console.log(text.toUpperCase()); // "  HELLO, WORLD!  "
```

## `toLowerCase()`

```js
console.log(text.toLowerCase()); // "  hello, world!  "
```

## `trim()`

Removes whitespace from both ends — very useful for cleaning up user input.

```js
console.log(text.trim()); // "Hello, World!"
```

## `includes()`

Checks whether a string contains a substring.

```js
console.log(text.includes("World")); // true
```

## `slice()`

Extracts a portion of a string using start/end indexes. Accepts negative numbers (counting from the end).

```js
const word = "JavaScript";
console.log(word.slice(0, 4));  // "Java"
console.log(word.slice(-6));    // "Script" — last 6 characters
```

## `substring()`

Similar to `slice()`, but doesn't support negative indexes (treats them as `0`).

```js
console.log(word.substring(0, 4)); // "Java"
```

## `charAt()`

Returns the character at a specific index.

```js
console.log(word.charAt(0)); // "J"
console.log(word[0]);        // "J" — bracket access works too
```

## Template literals

Backtick-quoted strings that support embedded expressions (`${...}`) and multi-line text — the modern way to build strings.

```js
const name = "Ravi";
const age = 29;

const message = `${name} is ${age} years old.`;
console.log(message); // "Ravi is 29 years old."

const multiline = `Line one
Line two`;
console.log(multiline);
```

## `replace()`

Replaces the first match of a substring (or regex) with something else.

```js
console.log("I like cats".replace("cats", "dogs")); // "I like dogs"

// Use a regex with the /g flag to replace ALL matches:
console.log("a-b-c".replace(/-/g, " ")); // "a b c"
```

## Try it yourself

```js
const messy = "   javaScript is FUN!   ";
// Trim it, then make it lowercase, then check if it includes "fun".
// Finally, use a template literal to log: "Cleaned: {result}"
```

Next up: [18. Scope & Closures](18-scope-and-closures.md) →
