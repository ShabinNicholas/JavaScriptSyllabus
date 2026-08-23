# 19. Timers

Timers let you run code after a delay, or repeatedly on an interval.

## `setTimeout()`

Runs a function **once**, after a delay (in milliseconds).

```js
console.log("Start");

setTimeout(() => {
  console.log("This runs after 2 seconds");
}, 2000);

console.log("End");
// Logs: "Start", "End", then (2 seconds later) "This runs after 2 seconds"
// Note: setTimeout doesn't pause the program — the rest of the code keeps running.
```

## `setInterval()`

Runs a function **repeatedly**, every X milliseconds, until stopped.

```js
let count = 0;

const intervalId = setInterval(() => {
  count++;
  console.log(`Tick ${count}`);
}, 1000);
// Logs "Tick 1", "Tick 2", "Tick 3"... every second, forever (until stopped)
```

## `clearTimeout()`

Cancels a pending `setTimeout()` before it fires — you need the ID that `setTimeout()` returned.

```js
const timeoutId = setTimeout(() => {
  console.log("You'll never see this");
}, 5000);

clearTimeout(timeoutId); // cancelled before it had a chance to run
```

## `clearInterval()`

Stops a running `setInterval()` — same idea, using the ID `setInterval()` returned.

```js
const id = setInterval(() => console.log("tick"), 1000);

setTimeout(() => {
  clearInterval(id); // stop the interval after 5 seconds
  console.log("Interval stopped.");
}, 5000);
```

## Try it yourself

```js
// Build a simple countdown: starting at 5, log the number every second,
// counting down to 1, then log "Liftoff!" and stop the interval.
// Hint: use setInterval + clearInterval together.
```

Next up: [20. Optional Chaining & Nullish Coalescing](20-optional-chaining-nullish-coalescing.md) →
