# Asynchronous Programming in JavaScript 

## What is Asynchronous Programming?

Asynchronous programming means your program can start a task and continue executing other code without waiting for that task to finish.

This is important in Node.js because it uses a single-threaded model. Instead of blocking execution, it handles multiple operations efficiently using asynchronous behavior.

---

## Synchronous vs Asynchronous

### Synchronous (Blocking)

* Executes line by line
* Waits for each operation to complete

```js
const data = fs.readFileSync('file.txt', 'utf-8');
console.log(data);
console.log("Done");
```

Output:

```
file content
Done
```

---

### Asynchronous (Non-blocking)

* Starts a task and continues execution
* Result is handled later

```js
fs.readFile('file.txt', 'utf-8', (err, data) => {
    console.log(data);
});
console.log("Done");
```

Output:

```
Done
file content appears later
```

---

## Callbacks

A callback is a function passed as an argument that is executed later.

```js
function fetchData(callback) {
    setTimeout(() => {
        callback("Data received");
    }, 1000);
}

fetchData((data) => {
    console.log(data);
});
```

### Problem: Callback Hell

Too many nested callbacks make code difficult to read and maintain.

---

## Promises

A Promise represents a value that will be available in the future.

### States:

* Pending
* Resolved
* Rejected

```js
const promise = new Promise((resolve, reject) => {
    resolve("Success");
});

promise
    .then(result => console.log(result))
    .catch(err => console.log(err));
```

---

## Promise Chaining

```js
fetchData()
    .then(data => processData(data))
    .then(result => console.log(result))
    .catch(err => console.log(err));
```

This avoids nested callbacks and improves readability.

---

## Async / Await

Async/await is built on top of Promises and allows writing asynchronous code in a synchronous style.

```js
async function getData() {
    try {
        const data = await fetchData();
        console.log(data);
    } catch (err) {
        console.log(err);
    }
}
```

---

## Event Loop (Basic Idea)

Node.js handles asynchronous operations using the event loop:

1. Executes synchronous code first
2. Sends asynchronous tasks to the system (file system, APIs, etc.)
3. When tasks complete, callbacks are queued
4. The event loop executes them when the call stack is free

---

## Streams

Streams are used to handle large data efficiently.

```js
fs.createReadStream('file.txt')
  .on('data', chunk => console.log(chunk))
  .on('end', () => console.log("Done"));
```

Advantages:

* Processes data in chunks
* Memory efficient
* Works asynchronously

---

## Error Handling

### Callbacks

```js
if (err) console.log(err);
```

### Promises

```js
.catch(err => console.log(err));
```

### Async/Await

```js
try {
    await something();
} catch (err) {
    console.log(err);
}
```

---

## Comparison

| Feature        | Callback  | Promise | Async/Await |
| -------------- | --------- | ------- | ----------- |
| Readability    | Low       | Medium  | High        |
| Error Handling | Difficult | Better  | Best        |
| Code Structure | Nested    | Linear  | Clean       |

---

## When to Use What

* Callbacks: simple and small tasks
* Promises: moderate complexity
* Async/Await: complex workflows
* Streams: large data processing

---

## Key Points

* Node.js is non-blocking and event-driven
* Asynchronous programming improves performance
* Promises reduce callback nesting
* Async/await improves readability
* Streams are useful for handling large files

---

## Summary

Asynchronous programming allows Node.js to handle multiple operations efficiently without waiting for each task to complete. Understanding callbacks, promises, async/await, and streams is essential for building scalable applications.

---
