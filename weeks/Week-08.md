# Week 08 — Advanced React

## Goal
Structure larger React applications with routing, shared state and measured performance work.

## Learning Objectives
- Implement nested routes and navigation with React Router.
- Choose Context or Redux Toolkit based on state needs.
- Profile before optimizing rendering or bundle work.

## Topics and Concepts
React Router, route parameters, layouts, Context, reducers, Redux Toolkit, memoization, lazy loading, error boundaries, forms and performance profiling.

## Resources
- **Official documentation:** [React Router](https://reactrouter.com/home), [Redux Toolkit](https://redux-toolkit.js.org/), [React performance](https://react.dev/reference/react/memo).
- **Course/video:** [Redux Essentials](https://redux.js.org/tutorials/essentials/part-1-overview-concepts).
- **Practice/book:** [React DevTools](https://react.dev/learn/react-developer-tools), *Fullstack React*.

## Daily Plan
| Day | Focus |
|---|---|
| Monday | Routing, layouts and route parameters. |
| Tuesday | Context and reducer-based state. |
| Wednesday | Redux Toolkit slices and async state. |
| Thursday | Performance profiling and memoization trade-offs. |
| Friday | Lazy loading, errors and loading routes. |
| Saturday | Build projects. |
| Sunday | Audit state ownership and interaction accessibility. |

## Interview Questions
1. When is Context insufficient for application state?
2. Why can memoization make an application worse?
3. How do route-level loading and error states improve UX?

## Mini Projects
1. **Admin Dashboard** — advanced, 14h. Protected layout, metrics and tables. *Skills:* routing, state. *Extension:* role-aware navigation.
2. **Chat App UI** — advanced, 14h. Conversation and presence interface. *Skills:* shared state. *Extension:* optimistic messages.
3. **Kanban Board** — advanced, 16h. Board with columns and cards. *Skills:* reducer/Redux. *Extension:* keyboard drag alternatives.

## Revision and Checklist
- [ ] Navigation supports browser back/forward correctly.
- [ ] Shared state has a documented owner.
- [ ] I profiled before applying optimization.
