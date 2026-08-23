# 11. Events

Events are how JavaScript reacts to things happening on a page — clicks, key presses, form submissions, and more.

## `onclick`

The simplest way to respond to a click, set directly on an element.

```html
<button id="myButton">Click me</button>
```

```js
const button = document.getElementById("myButton");

button.onclick = function () {
  alert("Button was clicked!");
};
```

You'll also see it inline in HTML (works, but mixing JS into HTML like this is generally discouraged):

```html
<button onclick="alert('Clicked!')">Click me</button>
```

## Event handler function

The more flexible, modern approach is `addEventListener()` — it lets you attach **multiple** handlers to the same element and supports many event types (`click`, `keydown`, `submit`, `mouseover`, etc.).

```js
function handleClick() {
  console.log("Button clicked!");
}

button.addEventListener("click", handleClick);
```

Using an anonymous or arrow function inline:

```js
button.addEventListener("click", () => {
  console.log("Clicked via arrow function!");
});
```

Removing a handler (only works if you kept a reference to the named function):

```js
button.removeEventListener("click", handleClick);
```

The event object gives you details about what happened:

```js
button.addEventListener("click", (event) => {
  console.log("Event type:", event.type);   // "click"
  console.log("Target element:", event.target); // the button itself
});
```

## Try it yourself

```html
<input id="nameInput" placeholder="Type your name" />
<p id="output"></p>
```

```js
// Add a "keyup" event listener to #nameInput.
// On every keystroke, update #output's textContent to say "Hello, {value}!"
```

Next up: [12. DOM Manipulation](12-dom-manipulation.md) →
