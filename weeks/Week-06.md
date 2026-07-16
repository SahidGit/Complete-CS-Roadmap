# Week 06 — TypeScript

## Goal
Use static types to make JavaScript code easier to understand and safer to change.

## Learning Objectives
- Model domain data with types, interfaces and unions.
- Write reusable generic functions and narrow unknown values.
- Configure a strict TypeScript project and migrate small JavaScript modules.

## Topics and Concepts
Inference, annotations, interfaces, type aliases, unions, narrowing, generics, utility types, modules, `tsconfig`, strict mode and runtime validation.

## Resources
- **Official documentation:** [TypeScript Handbook](https://www.typescriptlang.org/docs/handbook/intro.html), [TS Playground](https://www.typescriptlang.org/play).
- **Course/video:** [TypeScript YouTube](https://www.youtube.com/@MicrosoftDeveloper).
- **Practice/book:** [Type Challenges](https://github.com/type-challenges/type-challenges), *Programming TypeScript* by Boris Cherny.

## Daily Plan
| Day | Focus |
|---|---|
| Monday | Inference, annotations and strict configuration. |
| Tuesday | Objects, interfaces and unions. |
| Wednesday | Narrowing, functions and errors. |
| Thursday | Generics and utility types. |
| Friday | Convert a JavaScript module with runtime boundaries. |
| Saturday | Build projects. |
| Sunday | Review compiler messages and simplify types. |

## Interview Questions
1. Why does TypeScript not remove the need for runtime validation?
2. When would you prefer a union over an interface hierarchy?
3. What problem do generics solve?

## Mini Projects
1. **Task Manager** — intermediate, 8h. Typed task state and filters. *Skills:* unions, modules. *Extension:* add import/export validation.
2. **Inventory App** — intermediate, 10h. Products, stock and transactions. *Skills:* generics, data models. *Extension:* add low-stock alerts.
3. **JS-to-TS Migration** — intermediate, 6h. Convert a Week 5 project. *Skills:* incremental migration. *Extension:* enable every strict compiler option.

## Revision and Checklist
- [ ] Strict mode is enabled.
- [ ] I used `unknown`, not `any`, for untrusted values.
- [ ] Types reflect business rules rather than only syntax.
