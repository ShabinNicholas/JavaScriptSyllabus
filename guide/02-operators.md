# 2. Operators

Operators let you combine, compare, and transform values.

## Arithmetic operators

```js
console.log(5 + 2);   // 7   addition
console.log(5 - 2);   // 3   subtraction
console.log(5 * 2);   // 10  multiplication
console.log(5 / 2);   // 2.5 division
console.log(5 % 2);   // 1   remainder ("modulo") — great for "is this even?" checks
console.log(5 ** 2);  // 25  exponent (5 to the power of 2)
```

## Assignment operators

Shorthand for "do the math, then save it back into the same variable."

```js
let total = 10;
total += 5;  // same as: total = total + 5   -> 15
total -= 3;  // same as: total = total - 3   -> 12
total *= 2;  // same as: total = total * 2   -> 24
total /= 4;  // same as: total = total / 4   -> 6
```

## Comparison operators

```js
5 == "5";    // true  — checks value only, converts types first ("loose" equality)
5 === "5";   // false — checks value AND type, no conversion ("strict" equality)
5 != "5";    // false
5 !== "5";   // true
```

**Rule of thumb:** always use `===` and `!==`. The loose versions (`==`, `!=`) silently convert types and cause subtle bugs.

## Relational operators

```js
10 > 5;    // true
10 < 5;    // false
10 >= 10;  // true
10 <= 9;   // false
```

## Logical operators

```js
true && false;   // false — AND: both sides must be true
true || false;   // true  — OR: at least one side must be true
!true;            // false — NOT: flips the boolean

// Real-world example: only show the discount if logged in AND has a coupon
const canGetDiscount = isLoggedIn && hasCoupon;
```

## Ternary (conditional) operator

A compact one-line `if...else`.

```js
const age = 20;
const canVote = age >= 18 ? "Yes" : "No";
// condition ? valueIfTrue : valueIfFalse
console.log(canVote); // "Yes"
```

## Increment / Decrement

```js
let count = 0;
count++; // same as count = count + 1  -> 1
count--; // same as count = count - 1  -> 0
```

## Try it yourself

```js
// Given a number `n`, use the modulo operator to check if it's even or odd,
// then use a ternary to store the result ("even" or "odd") in a variable.
```

Next up: [3. Conditional Statements](03-conditional-statements.md) →
