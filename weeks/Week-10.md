# Week 10 — MongoDB, Mongoose and Deployment

## Goal
Persist application data, deploy a full-stack project and operate it with safe configuration.

## Learning Objectives
- Model documents, indexes and relationships in MongoDB.
- Use Mongoose schemas, validation and query patterns.
- Deploy frontend and API services with environment-specific configuration.

## Topics and Concepts
Documents and collections, CRUD, indexes, embedding versus referencing, Mongoose schemas/models, validation, pagination, environment variables, logging, CORS, deployment and monitoring basics.

## Resources
- **Official documentation:** [MongoDB docs](https://www.mongodb.com/docs/), [MongoDB University](https://learn.mongodb.com/), [Mongoose docs](https://mongoosejs.com/docs/), [OWASP configuration guidance](https://cheatsheetseries.owasp.org/).
- **Course/video:** [MongoDB YouTube](https://www.youtube.com/@MongoDB).
- **Practice/book:** [MongoDB VS Code Playground](https://www.mongodb.com/docs/mongodb-vscode/playgrounds/), *MongoDB: The Definitive Guide*.

## Daily Plan
| Day | Focus |
|---|---|
| Monday | Documents, collections, queries and indexes. |
| Tuesday | Schema design: embedding versus referencing. |
| Wednesday | Mongoose models, validation and pagination. |
| Thursday | Connect API, database and client safely. |
| Friday | Deploy, configure environments and inspect logs. |
| Saturday | Build projects. |
| Sunday | Run a production-readiness review and retrospective. |

## Interview Questions
1. When should data be embedded rather than referenced?
2. What trade-off does an index make?
3. Why must environment variables be validated at startup?

## Mini Projects
1. **Full-Stack Notes App** — advanced, 24h. React client and authenticated notes API. *Skills:* complete vertical slice. *Extension:* full-text search.
2. **Blog Backend** — advanced, 14h. Posts, authors, tags and drafts. *Skills:* schema design. *Extension:* publish scheduling.
3. **Authentication System** — advanced, 14h. Production-style auth service. *Skills:* secure configuration. *Extension:* email verification flow.

## Revision and Checklist
- [ ] Query patterns informed the schema design.
- [ ] Database and deployment credentials are not in source control.
- [ ] A deployed application has a health check and clear error logs.
- [ ] I wrote a final portfolio retrospective.
