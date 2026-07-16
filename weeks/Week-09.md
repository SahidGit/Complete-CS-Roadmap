# Week 09 — Node.js, Express and REST APIs

## Goal
Design and implement small, secure HTTP APIs with clear contracts and error handling.

## Learning Objectives
- Use Node modules, environment variables and asynchronous I/O.
- Design RESTful routes, status codes and request validation.
- Implement password hashing and JWT-based authentication safely.

## Topics and Concepts
Node runtime, npm, Express middleware, routing, REST conventions, JSON APIs, validation, error middleware, HTTP status codes, password hashing, JWT, authorization and API documentation.

## Resources
- **Official documentation:** [Node.js API](https://nodejs.org/docs/latest/api/), [Express guide](https://expressjs.com/), [OWASP Authentication Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Authentication_Cheat_Sheet.html).
- **Course/video:** [Node.js Learn](https://nodejs.org/en/learn), [Hussein Nasser](https://www.youtube.com/@hnasr).
- **Practice/book:** [Postman Learning Center](https://learning.postman.com/), *Node.js Design Patterns*.

## Daily Plan
| Day | Focus |
|---|---|
| Monday | Node modules, npm scripts and configuration. |
| Tuesday | Express routes, middleware and REST conventions. |
| Wednesday | Validation, errors and API documentation. |
| Thursday | Password hashing, JWT and authorization boundaries. |
| Friday | Test manually with an API client; audit status codes. |
| Saturday | Build projects. |
| Sunday | Threat-model inputs, secrets and access control. |

## Interview Questions
1. What distinguishes authentication from authorization?
2. Why should passwords be hashed rather than encrypted?
3. What makes an HTTP API idempotent?

## Mini Projects
1. **Authentication API** — advanced, 12h. Register, sign in and protected profile. *Skills:* hashing, JWT. *Extension:* refresh-token rotation.
2. **Task API** — advanced, 12h. CRUD tasks with validation and ownership. *Skills:* REST design. *Extension:* pagination and filtering.
3. **Inventory API** — advanced, 14h. Products and stock movements. *Skills:* domain modeling. *Extension:* transaction audit log.

## Revision and Checklist
- [ ] Secrets are loaded from environment variables and never committed.
- [ ] Invalid input produces useful, non-sensitive errors.
- [ ] Protected routes enforce ownership as well as authentication.
