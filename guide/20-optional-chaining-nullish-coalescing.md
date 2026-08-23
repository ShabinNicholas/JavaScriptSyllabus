# 20. Optional Chaining & Nullish Coalescing

Two small operators that make working with uncertain data — like an API response — much safer and shorter to write.

## Optional chaining (`?.`)

Safely accesses a nested property, **without throwing an error** if something along the way is `null` or `undefined`. Instead, the whole expression short-circuits to `undefined`.

```js
const user = {
  name: "Alex",
  address: {
    city: "Denver",
  },
};

console.log(user.address?.city);   // "Denver"
console.log(user.contact?.email);  // undefined — no error, even though `contact` doesn't exist

// Compare to the old, verbose way of guarding against this:
// const email = user.contact && user.contact.email;
```

It also works for calling a method that might not exist:

```js
user.greet?.(); // does nothing, no error — `greet` isn't a function on user
```

And for array access:

```js
const users = [];
console.log(users[0]?.name); // undefined, not a crash
```

## Nullish coalescing (`??`)

Provides a fallback value, but **only** when the left side is `null` or `undefined` — unlike `||`, which also falls back on `0`, `""`, or `false` (values that are "falsy" but still meaningfully set).

```js
const score = 0;

console.log(score || 100); // 100 <- wrong! 0 is a valid score, but || treats it as falsy
console.log(score ?? 100); // 0   <- correct! ?? only cares about null/undefined
```

```js
let username; // undefined
console.log(username ?? "Guest"); // "Guest"

username = "";
console.log(username ?? "Guest"); // "" — empty string is NOT null/undefined, so it's kept
```

## Combining both for safe API data access

This pairing is extremely common when working with data from an API, where fields might be missing.

```js
function getDisplayName(apiResponse) {
  return apiResponse?.user?.profile?.displayName ?? "Anonymous";
}

console.log(getDisplayName({ user: { profile: { displayName: "Nova" } } })); // "Nova"
console.log(getDisplayName({ user: {} }));                                   // "Anonymous"
console.log(getDisplayName(null));                                           // "Anonymous"
```

Without these operators, that same safety would require a much longer chain of `&&` checks.

## Try it yourself

```js
const response = { data: { items: [] } };
// Safely read response.data.items[0].name, falling back to "No item" if anything is missing.
// Then test it against a response where `data` itself is undefined.
```

Next up: [21. Modules](21-modules.md) →
