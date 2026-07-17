# Backend Reference

Use [Node.js Documentation](https://nodejs.org/docs/latest/api/) and [Express Guide](https://expressjs.com/) as primary resources for backend architecture. Design explicit input validation, proper error handling, and robust environment variables from your first server API.

---

## 🛠️ Technology Guides

| Technology | Reference Guide | Description |
| :--- | :--- | :--- |
| **Node.js** | [NodeJS.md](./NodeJS.md) | Single-threaded architecture, event loop phases, buffers/streams, file systems, path resolver, modules (ESM vs CJS). |
| **Express.js** | [Express.md](./Express.md) | Route handlers, request/response models, custom router structures, global error handlers, and security implementations. |
| **MongoDB** | [MongoDB.md](./MongoDB.md) | NoSQL databases, Mongoose schemas, CRUD query filters, pre/post middleware hooks, relationship patterns, and aggregations. |

---

## 📺 Recommended YouTube Channels

- **Sheryians Coding School** – Detailed Node.js and Express backend series (in Hindi/English). [Channel](https://www.youtube.com/@sheryianscodingschool) | [Playlist](https://www.youtube.com/playlist?list=PLsheryianBackend)
- **Chai aur Code** – Premium step-by-step backend web development playlist (in Hindi). [Channel](https://www.youtube.com/@chaiaurcode) | [Backend Playlist](https://www.youtube.com/playlist?list=PLu0W_9lII9agq5trB9hYd076xSenVyGN3)
- **Hussein Nasser** – Exceptional deep dives into databases, HTTP network layers, proxy routing, and backend systems architecture. [Channel](https://www.youtube.com/@hnasr)
- **freeCodeCamp** – Long-form structured tutorials on Express API projects, authentication schemes, and databases. [Channel](https://www.youtube.com/@freecodecamp)

---

## 📋 Suggested Tasks

- **Before Writing Backend Code**: Understand the HTTP Request/Response model lifecycle, status codes (2xx, 3xx, 4xx, 5xx), and standard CORS policies.
- **After Completing a Concept**: Build a secure JSON REST API connecting to a local/atlas MongoDB instance. Implement authentication (JWT), request validation (Zod/Joi), and deploy to a cloud host (Render, Railway, or Fly.io).

---

## 📁 Project Idea Repositories

- **App Ideas Collection** – [GitHub Repo](https://github.com/florinpop17/app-ideas)
- **RealWorld conduit API Specs** – [GitHub Repo](https://github.com/gothinkster/realworld)
- **Public APIs List** – [GitHub Repo](https://github.com/public-apis/public-apis)

---

## 🤖 Advanced Backend & AI Projects

Build modern backend portfolio items by integrating Generative AI (LLMs) and advanced systems (caching, queues):

1. **AI-Powered Real-Time Chat Assistant**
   - **Goal**: Build a real-time chat application where users can communicate via WebSockets, and tag an AI assistant (`@ai`) to generate answers using conversation history context.
   - **Stack**: React, Node.js, Express, Socket.io, Redis (history caching), Google Gemini API.
   - **Reference Video**: [Sheryians Coding School: Gen AI & MERN Integration](https://www.youtube.com/@sheryians)

2. **RAG-Based Document Search Engine (Retrieval-Augmented Generation)**
   - **Goal**: Create an API that allows users to upload PDF manuals, extracts and chunks text, converts text to vector embeddings, stores them in ChromaDB, and performs semantic search to answer user queries using an LLM.
   - **Stack**: Node.js, Express, LangChain, ChromaDB, Google Gemini API, Multer.
   - **Reference Playlist**: [Sheryians AI School: RAG & Vector DB Series](https://www.youtube.com/@SheryiansAI)

3. **Multi-Agent Developer Assistant API**
   - **Goal**: Design a coordinator API that breaks down user programming tasks (e.g. "Create a router file and write standard tests"), delegates code generation to a developer agent, code inspection to a reviewer agent, and returns the audited code.
   - **Stack**: Node.js/Python, LangGraph, Google Gemini API, Zod Schema Validation.
   - **Reference Playlist**: [Sheryians AI School: AI Agents & Tool Calling](https://www.youtube.com/@SheryiansAI)

