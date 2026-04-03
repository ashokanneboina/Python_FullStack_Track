# JavaScript Debugging Guide 
---

# 1. Console Methods

## console.log()

* Prints general information to the console
* Used to track values and execution flow

```js
console.log("Hello World");
```

---

## console.error()

* Displays error messages (usually in red)
* Helps highlight critical issues

```js
console.error("Something went wrong!");
```

---

## console.warn()

* Shows warning messages
* Indicates possible issues

```js
console.warn("This might cause an issue.");
```

---

## console.info()

* Informational messages
* Similar to console.log()

```js
console.info("Execution started");
```

---

## console.table()

* Displays arrays/objects in table format

```js
const users = [
  { name: "Ashok", age: 21 },
  { name: "John", age: 25 }
];

console.table(users);
```

---

## console.debug()

* Used for debugging-specific logs

```js
console.debug("Debug value:", 100);
```

---

## debugger

* Pauses execution at that line
* Used in DevTools for step-by-step debugging

```js
debugger;
```

---

# 2. Debugging Strategies

## 1. Logging Strategy

```js
console.log("value:", x);
console.error("error:", err);
console.warn("warning");
```

* Track inputs → process → output

---

## 2. Isolation Strategy

```js
console.log(a);
console.log(b);
console.log(calculate(a, b));
```

* Find exact line where bug occurs

---

## 3. Binary Search Debugging

```js
// part2();
part1();
```

* Disable parts to narrow issue

---

## 4. Use debugger

```js
debugger;
```

* Inspect variables
* Step through execution

---

## 5. Validate Assumptions

```js
console.log(typeof value);
console.log(value === undefined);
```

* Check data types and values

---

## 6. Check Edge Cases

```js
calculateTotal(0, 0);
calculateTotal(-1, 5);
calculateTotal(null, 10);
```

---

## 7. Read Errors Properly

Example:

```
Uncaught TypeError: x is not a function
```

* Check line number
* Check variable type

---

## 8. Trace Execution Flow

```js
console.log("Step 1");
console.log("Step 2");
console.log("Step 3");
```

---

## 9. Compare Expected vs Actual

```js
console.log("Expected:", 500);
console.log("Actual:", result);
```

---

## 10. Simplify Code

```js
let price = 100;
processOrder(price);
```

---

## 11. Check Conditions

```js
if (value === 10) // correct
```

---

## 12. Verify Inputs/Outputs

```js
function sum(a, b) {
  console.log("Inputs:", a, b);
  return a + b;
}
```

---

# 3. Debugging Example 

## Buggy Code

```js
function calculateTotal(price, quantity) {
  debugger;

  console.log("Price:", price);
  console.log("Quantity:", quantity);

  let total = price + quantity; // Bug

  console.log("Total:", total);

  return total;
}

function printTotal() {
  let result = calculateTotal(100, 5);

  console.log("Expected:", 500);
  console.log("Actual:", result);
}

printTotal();
```

---

## Fix

```js
function calculateTotal(price, quantity) {
  return price * quantity;
}
```

---

## Final Output

```
Expected: 500
Actual: 500
```

---

# Final Rule

> Don’t guess bugs → observe them using logs and debugger
