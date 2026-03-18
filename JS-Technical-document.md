

# JavaScript Fundamentals 

## Data Types

JavaScript has two categories of data types:

* **Primitive (immutable)**:
  `string`, `number`, `boolean`, `null`, `undefined`, `symbol`, `bigint`

* **Non-Primitive (mutable)**:
  `object`, `array`, `function`

---

## Scope

Scope determines where a variable is accessible.

* **Global Scope** → accessible everywhere
* **Function Scope** → accessible only inside a function
* **Block Scope** → accessible inside `{}` (used by `let` and `const`)

---

## let vs var vs const

* `var`: function-scoped, hoisted, can be redeclared
* `let`: block-scoped, can be updated but not redeclared
* `const`: block-scoped, cannot be reassigned

### Why avoid `var`?

* No block scope → leads to unexpected behavior
* Hoisting confusion
* Easier to introduce bugs

---

## Why Global Variables are Bad

* Increase chances of name conflicts
* Difficult to debug
* Break modularity and maintainability

---

## Truthy and Falsy Values

Falsy values:

```js
false, 0, "", null, undefined, NaN
```

All other values are **truthy**.

---

## Function Hoisting

Function declarations are hoisted:

```js
greet();

function greet() {
  console.log("Hello");
}
```

---

## No Return Statement

If a function does not return anything:

```js
function test() {}
console.log(test()); // undefined
```

---

## Function Declarations

```js
// Named function
function add(a, b) { return a + b; }

// Anonymous function
const add = function(a, b) { return a + b; };

// Arrow function
const add = (a, b) => a + b;
```

---

## Pass by Value vs Reference

```js
// Primitive → Pass by value
let a = 10;
let b = a;
b = 20; // a remains 10

// Object → Pass by reference
let obj1 = { x: 1 };
let obj2 = obj1;
obj2.x = 2; // obj1.x becomes 2
```

---

## Loops in JavaScript

```js
// Basic for loop
for (let i = 0; i < 5; i++) {}

// for...in → iterates keys
for (let key in obj) {}

// for...of → iterates values
for (let val of arr) {}

// forEach → executes function for each element
arr.forEach(item => {})

// while loop
while (condition) {}
```

---

## Using MDN

* Best documentation source
* Search: `MDN + concept`
  Example: `MDN Array.map`

---

# Array Utility Methods

## Basics

```js
arr.push(1)      // mutable → adds element
arr.pop()        // mutable → removes last element
arr.concat([2])  // immutable → returns new array
arr.slice(1, 3)  // immutable → extracts portion
arr.splice(1,1)  // mutable → modifies array
arr.join(",")    // immutable → converts to string
arr.flat()       // immutable → flattens array
```

## Finding Elements

```js
arr.find(x => x > 2)       // returns first match
arr.indexOf(2)             // index of value
arr.includes(2)            // true/false
arr.findIndex(x => x > 2)  // index of match
```

## Higher Order Functions

```js
arr.forEach(x => console.log(x)) // no return

arr.map(x => x * 2)              // transforms array

arr.filter(x => x > 2)           // filters elements

arr.reduce((acc, cur) => acc + cur, 0) // reduces to single value

arr.sort()                       // sorts array (mutable)
```

## Method Chaining

```js
arr
  .filter(x => x > 2)
  .map(x => x * 2)
```

---

# String Methods (Immutable)

Strings are immutable, meaning methods return new strings:

```js
str.toUpperCase()
str.toLowerCase()
str.includes("a")
str.slice(1, 3)
str.replace("a", "b")
str.split(",")
```

---

# Object Methods

```js
Object.keys(obj)      // returns keys
Object.values(obj)    // returns values
Object.entries(obj)   // key-value pairs

Object.assign({}, obj) // creates shallow copy (immutable)
```

---

## forEach vs map/filter/reduce

* `forEach` → perform actions (no return)
* `map` → transform array
* `filter` → select elements
* `reduce` → compute single result

---

## Mutable vs Immutable

* **Mutable**: modifies original array (`push`, `splice`)
* **Immutable**: returns new array (`map`, `filter`, `slice`)

---

# Error Handling

```js
try {
  riskyFunction();
} catch (error) {
  console.error(error);
}
```

---

## Throwing Errors

```js
throw new Error("Something went wrong"); // recommended

throw "Error message"; // not recommended
```

**Why?**
`Error` objects provide stack trace and debugging info.

---

## Debugging & Stack Trace

* Read error message carefully
* Check file and line number
* Trace function calls
* Practice daily

---

## Spread Operator

```js
let newArr = [...arr];
let newObj = { ...obj };
```

---

## Template Literals

```js
`Hello ${name}`
```

---

## Default Parameters

```js
function greet(name = "Guest") {}
```

---

## Destructuring

```js
const { name } = obj;
const [a, b] = arr;
```

---

## Closures

A closure allows a function to access variables from its outer scope:

```js
function outer() {
  let x = 10;
  return function inner() {
    console.log(x);
  };
}
```

---

## Arrow vs Regular Functions

* Arrow → no `this`, shorter syntax
* Regular → has its own `this`

---

## === vs ==

* `===` → strict comparison (recommended)
* `==` → type coercion (can cause bugs)

---

## undefined Check

```js
value === undefined // safe
!value              // unsafe (covers falsy values)
```

---

## null vs undefined

* `undefined` → variable not assigned
* `null` → explicitly empty

---

## Modules (CommonJS)

```js
// export
module.exports = myFunction;

// import
const myFunction = require("./file");
```

---

## Console Methods

```js
console.log()    // general logs
console.error()  // errors
console.warn()   // warnings
console.info()   // info messages
```

---

## Best Practices

* Use proper indentation
* Use meaningful variable names
* Prefer `const` over `let`
* Avoid global variables
* Keep functions small and reusable

---

## Functions as Arguments

```js
function execute(fn) {
  fn();
}
```

---

## Named vs Anonymous Functions

* Named → reusable, better debugging
* Anonymous → used inline

---

## Variable Arguments

```js
function sum(...args) {
  return args.reduce((a, b) => a + b);
}
```

---

## Debugging Strategies

* Use `console.log()` wisely
* Use browser debugger
* Break problems into smaller parts
* Understand stack traces

