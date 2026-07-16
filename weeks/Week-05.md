# Week 05 — Advanced JavaScript and Browser APIs

## Goal
Build resilient data-driven interfaces using asynchronous JavaScript and browser persistence.

## Learning Objectives
- Explain promises, `async`/`await` and the event loop.
- Fetch remote data with loading, empty and error states.
- Apply closures, prototypes and local storage appropriately.

## Topics and Concepts
Promises, async/await, fetch, HTTP errors, `AbortController`, JSON, localStorage, closures, prototypes, classes, event loop and defensive input handling.

## Resources
- **Official documentation:** [MDN Promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises), [Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API), [Web Storage](https://developer.mozilla.org/en-US/docs/Web/API/Web_Storage_API).
- **Course/video:** [freeCodeCamp](https://www.youtube.com/@freecodecamp).
- **Practice/book:** [JavaScript30](https://javascript30.com/), *You Don’t Know JS Yet*.

## Daily Plan
| Day | Focus |
|---|---|
| Monday | Promise states and async/await. |
| Tuesday | Fetch, JSON and HTTP failure handling. |
| Wednesday | Local storage and data serialization. |
| Thursday | Closures, prototypes and object behavior. |
| Friday | Event loop and cancellation. |
| Saturday | Build projects. |
| Sunday | Review network requests and edge cases. |

## Interview Questions
1. Why does `fetch` not reject for HTTP 404 responses?
2. What is a closure and when is it useful?
3. How do microtasks affect `async`/`await` execution?

## Mini Projects
1. **Movie App** — intermediate, 10h. Search and save films. *Skills:* API consumption. *Extension:* request cancellation.
2. **Quiz App** — intermediate, 8h. Timed questions with score persistence. *Skills:* state, storage. *Extension:* randomized question bank.
3. **Expense Tracker** — intermediate, 10h. Categorize transactions and totals. *Skills:* data modeling. *Extension:* CSV export.

## Revision and Checklist
- [ ] All network UIs show loading and meaningful errors.
- [ ] Persisted data is validated before use.
- [ ] I can explain a promise chain and its equivalent `async` function.
