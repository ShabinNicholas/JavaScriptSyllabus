# 7. Array Methods

Arrays come with a rich toolkit of built-in methods. These are some of the most useful tools in everyday JavaScript — worth memorizing.

> Sample data used throughout this page:
> ```js
> const numbers = [5, 12, 8, 130, 44];
> ```

## `map()`

Transforms every item and returns a **new array** of the same length.

```js
const doubled = numbers.map(n => n * 2);
console.log(doubled); // [10, 24, 16, 260, 88]
```

## `filter()`

Returns a **new array** with only the items that pass a test.

```js
const bigNumbers = numbers.filter(n => n > 10);
console.log(bigNumbers); // [12, 130, 44]
```

## `forEach()`

Runs a function for each item. Doesn't return anything — used for side effects like logging.

```js
numbers.forEach(n => console.log(n));
```

## `reduce()`

Boils an array down to a single value (a sum, an average, an object, anything).

```js
const total = numbers.reduce((sum, n) => sum + n, 0);
// sum starts at 0, then adds each number in turn
console.log(total); // 199
```

## `find()`

Returns the **first item** that matches a condition, or `undefined` if none do.

```js
const found = numbers.find(n => n > 10);
console.log(found); // 12
```

## `findIndex()`

Same as `find()`, but returns the **index** instead of the value (`-1` if not found).

```js
const index = numbers.findIndex(n => n > 10);
console.log(index); // 1
```

## `includes()`

Checks if a value exists in the array — returns `true`/`false`.

```js
console.log(numbers.includes(8));  // true
console.log(numbers.includes(99)); // false
```

## `indexOf()`

Returns the index of a value, or `-1` if it's not there.

```js
console.log(numbers.indexOf(8)); // 2
```

## `push()` / `pop()`

Add/remove from the **end** of an array.

```js
const stack = [1, 2, 3];
stack.push(4);   // [1, 2, 3, 4]
stack.pop();     // removes 4 -> [1, 2, 3]
```

## `shift()` / `unshift()`

Remove/add from the **beginning** of an array.

```js
const queue = [1, 2, 3];
queue.unshift(0); // [0, 1, 2, 3]
queue.shift();    // removes 0 -> [1, 2, 3]
```

## `slice()`

Returns a **copy** of a portion of the array. Doesn't change the original.

```js
const letters = ["a", "b", "c", "d", "e"];
console.log(letters.slice(1, 3)); // ["b", "c"]  (index 1 up to, not including, 3)
console.log(letters);             // unchanged
```

## `splice()`

Adds/removes items **in place**, mutating the original array.

```js
const nums = [1, 2, 3, 4, 5];
nums.splice(1, 2);          // removes 2 items starting at index 1 -> [1, 4, 5]
nums.splice(1, 0, "a", "b"); // insert without removing -> [1, "a", "b", 4, 5]
```

## `concat()`

Joins two or more arrays into a new one.

```js
const combined = [1, 2].concat([3, 4]);
console.log(combined); // [1, 2, 3, 4]
```

## `join()`

Turns an array into a string, with a separator of your choice.

```js
console.log(["a", "b", "c"].join("-")); // "a-b-c"
```

## `split()`

The opposite of `join()` — turns a string into an array (technically a String method, but they're a pair worth learning together).

```js
console.log("a-b-c".split("-")); // ["a", "b", "c"]
```

## `sort()`

Sorts **in place**. By default it sorts as strings — for numbers, pass a compare function.

```js
const nums2 = [40, 1, 5, 200];
nums2.sort();                       // [1, 200, 40, 5]  <- wrong! sorted as text
nums2.sort((a, b) => a - b);        // [1, 5, 40, 200]  <- correct numeric sort
```

## `reverse()`

Reverses the array **in place**.

```js
console.log([1, 2, 3].reverse()); // [3, 2, 1]
```

## `some()`

Returns `true` if **at least one** item passes the test.

```js
console.log(numbers.some(n => n > 100)); // true (130 qualifies)
```

## `every()`

Returns `true` only if **all** items pass the test.

```js
console.log(numbers.every(n => n > 0)); // true
```

## `flat()`

Flattens nested arrays into a single level.

```js
const nested = [1, [2, 3], [4, [5, 6]]];
console.log(nested.flat());    // [1, 2, 3, 4, [5, 6]]  — 1 level deep
console.log(nested.flat(2));   // [1, 2, 3, 4, 5, 6]    — 2 levels deep
```

## `Array.from()`

Creates an array from something array-*like* (a string, a Set, a NodeList).

```js
console.log(Array.from("hello")); // ["h", "e", "l", "l", "o"]
```

## `Array.isArray()`

Checks whether a value is actually an array (`typeof` won't tell you this — it just says `"object"`).

```js
console.log(Array.isArray([1, 2])); // true
console.log(Array.isArray("hi"));   // false
```

## `length` property

```js
console.log(numbers.length); // 5
```

## Try it yourself

```js
const prices = [12.5, 40, 3.2, 99, 7];
// Use filter() to get prices under $20.
// Use map() to apply a 10% discount to every price.
// Use reduce() to get the total of the discounted prices.
```

Next up: [8. Object Basics](08-object-basics.md) →
