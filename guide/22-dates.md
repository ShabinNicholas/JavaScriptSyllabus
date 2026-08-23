# 22. Dates

JavaScript's built-in `Date` object handles dates and times.

## Creating a date (`new Date()`)

```js
const now = new Date();          // current date and time
console.log(now);

const specific = new Date(2024, 5, 15); // June 15, 2024 — note: months are 0-indexed!
console.log(specific);

const fromString = new Date("2024-06-15"); // parsed from an ISO date string
console.log(fromString);
```

⚠️ Months are zero-indexed: `0` = January, `11` = December. This trips up almost everyone at least once.

## Getting values

```js
const date = new Date(2024, 5, 15, 14, 30); // June 15, 2024, 2:30 PM

console.log(date.getFullYear()); // 2024
console.log(date.getMonth());    // 5  (June — remember, 0-indexed)
console.log(date.getDate());     // 15 (day of the month)
console.log(date.getDay());      // 6  (day of the week, 0 = Sunday)
console.log(date.getHours());    // 14
console.log(date.getMinutes());  // 30
```

## Formatting a date

The raw `Date` object doesn't format nicely on its own — combine the getters, or use built-in formatting helpers.

```js
const date = new Date(2024, 5, 15);

// Manual formatting using the getters above:
const formatted = `${date.getMonth() + 1}/${date.getDate()}/${date.getFullYear()}`;
console.log(formatted); // "6/15/2024"

// Built-in, locale-aware formatting (no manual math needed):
console.log(date.toLocaleDateString());
// "6/15/2024" (format depends on the user's locale)

console.log(date.toLocaleDateString("en-US", {
  year: "numeric",
  month: "long",
  day: "numeric",
}));
// "June 15, 2024"
```

Comparing dates (dates can be compared like numbers — JavaScript converts them to timestamps):

```js
const today = new Date();
const deadline = new Date(2026, 11, 31);

console.log(deadline > today); // true, if today is before Dec 31, 2026
```

## Try it yourself

```js
// Create a Date for your next birthday this year.
// Log the month, day, and year separately using the getter methods.
// Then log it nicely formatted with toLocaleDateString().
```

Next up: [23. Working with Data](23-working-with-data.md) →
