# 12. DOM Manipulation

The **DOM** (Document Object Model) is how JavaScript "sees" your HTML page — as a tree of objects it can read and change.

## `getElementById()`

Grabs a single element by its `id` attribute.

```html
<h1 id="title">Original Title</h1>
```

```js
const title = document.getElementById("title");
console.log(title); // the <h1> element itself
```

## `textContent`

Reads or sets the plain text inside an element (safely — no HTML parsing).

```js
title.textContent = "Updated Title!";
console.log(title.textContent); // "Updated Title!"
```

## `value`

Reads or sets the current value of a form field (`<input>`, `<textarea>`, `<select>`).

```html
<input id="username" type="text" />
```

```js
const input = document.getElementById("username");

input.value = "guest123";        // set the field's value
console.log(input.value);        // "guest123" — read it back
```

## `innerHTML`

Reads or sets the HTML **markup** inside an element — not just plain text.

```js
const box = document.getElementById("title");
box.innerHTML = "<strong>Bold Title!</strong>";
```

⚠️ **Be careful with `innerHTML`.** If you ever insert text that came from a user (a comment, a search box, etc.), it can run malicious scripts — a vulnerability called XSS. Use `textContent` whenever you're just displaying text, and only use `innerHTML` with content you trust or have sanitized.

## Putting it together

```html
<button id="loadBtn">Load Name</button>
<p id="greeting"></p>
```

```js
const button = document.getElementById("loadBtn");
const greeting = document.getElementById("greeting");

button.addEventListener("click", () => {
  greeting.textContent = "Hello, welcome to the page!";
});
```

## Try it yourself

```html
<input id="colorInput" placeholder="Type a CSS color" />
<button id="applyBtn">Apply</button>
<div id="preview" style="width:100px;height:100px;border:1px solid #ccc;"></div>
```

```js
// When #applyBtn is clicked, set #preview's background color
// to whatever the user typed in #colorInput.
// Hint: document.getElementById("preview").style.backgroundColor = ...
```

Next up: [13. Web Storage](13-web-storage.md) →
