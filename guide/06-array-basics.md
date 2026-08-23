# 6. Array Basics

Arrays store ordered lists of values — perfect for collections like a shopping list, a set of scores, or rows of data.

## Creating an array `[]`

```js
const fruits = ["apple", "banana", "cherry"];
```

## Creating an array with `new Array()`

Rarely used in modern code — the `[]` syntax above is preferred — but you'll see it.

```js
const numbers = new Array(1, 2, 3);
console.log(numbers); // [1, 2, 3]
```

## Accessing elements by index

Arrays are zero-indexed — the first item is at position `0`.

```js
console.log(fruits[0]); // "apple"
console.log(fruits[2]); // "cherry"
console.log(fruits[5]); // undefined — index doesn't exist
```

## Array length property

```js
console.log(fruits.length); // 3
```

## Updating an element

```js
fruits[1] = "blueberry";
console.log(fruits); // ["apple", "blueberry", "cherry"]
```

## Adding an element (index / push)

```js
fruits[3] = "date";      // add by setting the next index directly
fruits.push("elderberry"); // add to the end (preferred, safer way)
console.log(fruits); // ["apple", "blueberry", "cherry", "date", "elderberry"]
```

## Looping with `for` loop

```js
for (let i = 0; i < fruits.length; i++) {
  console.log(fruits[i]);
}
```

## Looping with `for...of`

```js
for (const fruit of fruits) {
  console.log(fruit);
}
```

## Looping with `forEach()`

```js
fruits.forEach((fruit, index) => {
  console.log(`${index}: ${fruit}`);
});
```

See [Array Methods](07-array-methods.md) for a deeper look at `forEach` and friends.

## Nested / multidimensional arrays

An array of arrays — useful for grids, matrices, or tables.

```js
const grid = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9],
];

console.log(grid[1][2]); // 6 — row index 1, column index 2
```

## Array of objects

One of the most common patterns in real apps — a list of records.

```js
const users = [
  { name: "Ana", age: 30 },
  { name: "Ben", age: 25 },
];

console.log(users[0].name); // "Ana"

users.forEach(user => {
  console.log(`${user.name} is ${user.age} years old.`);
});
```

## Try it yourself

```js
// Create an array of your 3 favorite movies.
// Add a 4th movie with push().
// Loop over the array with forEach and log "I love {movie}" for each.
```

Next up: [7. Array Methods](07-array-methods.md) →
