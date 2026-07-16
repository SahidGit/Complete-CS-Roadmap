# Week 11: Advanced Node.js

## Goal
Master advanced Node.js concepts including the event loop, streams, buffers, and process management to build high-performance server applications.

## Learning Objectives
- Understand and optimize the Node.js event loop
- Work with streams for efficient data handling
- Manage buffers and binary data
- Implement child processes and worker threads
- Use file system APIs effectively
- Configure clustering for multi-core systems

## Estimated Study Hours
**40-45 hours** (6-7 hours/day)

## Prerequisites
- Node.js fundamentals (Week 1)
- JavaScript async/await and callbacks
- Basic command-line knowledge

## Daily Schedule
| Day | Focus | Duration |
|-----|-------|----------|
| Monday | Event Loop Deep Dive | 6h |
| Tuesday | Streams & Buffers | 6h |
| Wednesday | Process & Child Process | 6h |
| Thursday | File System & Cluster | 6h |
| Friday | Worker Threads & Performance | 6h |
| Saturday | Mini Projects | 5h |
| Sunday | Revision & Interview Prep | 5h |

## Topics

### 1. Node Event Loop
- Event Loop phases (timers, pending callbacks, idle, prepare, poll, check, close)
- Microtask vs Macrotask queues
- Event Loop visualization and debugging
- `setImmediate()` vs `setTimeout()` vs `process.nextTick()`
- Event Loop blocking prevention

### 2. Streams
- Stream types (Readable, Writable, Duplex, Transform)
- Stream events and error handling
- Piping and pipeline
- Creating custom streams
- Memory-efficient file processing

### 3. Buffer
- Buffer creation and manipulation
- Encoding/Decoding
- Buffer methods
- Memory management
- Binary data handling

### 4. Process
- Process object and properties
- Environment variables
- Exit codes
- Signal handling
- Process streams (stdin, stdout, stderr)

### 5. Child Process
- `spawn()` vs `fork()` vs `exec()` vs `execFile()`
- Inter-process communication (IPC)
- Process management
- Error handling

### 6. File System
- Synchronous vs Asynchronous operations
- Promises-based fs API
- File watching
- Recursive operations
- Permissions and stats

### 7. Cluster
- Cluster module basics
- Master-worker pattern
- Load balancing
- Process spawning
- Graceful shutdown

### 8. Worker Threads
- Worker thread creation
- Message passing
- Shared memory (SharedArrayBuffer)
- Performance considerations
- Use cases

## Official Docs
- [Node.js Official Documentation](https://nodejs.org/docs/)
- [Event Loop](https://nodejs.org/en/docs/guides/blocking-vs-non-blocking/)
- [Streams](https://nodejs.org/api/stream.html)
- [Buffer API](https://nodejs.org/api/buffer.html)
- [Process API](https://nodejs.org/api/process.html)
- [Child Processes](https://nodejs.org/api/child_process.html)
- [File System](https://nodejs.org/api/fs.html)
- [Cluster](https://nodejs.org/api/cluster.html)
- [Worker Threads](https://nodejs.org/api/worker_threads.html)

## Official GitHub Repositories
- [Node.js Repository](https://github.com/nodejs/node)
- [Node.js Examples](https://github.com/nodejs/examples)
- [Node.js Best Practices](https://github.com/goldbergyoni/nodebestpractices)

## Official YouTube Playlist
- [Node.js Advanced Concepts - Traversy Media](https://www.youtube.com/playlist?list=PLkAPA_Z-zx_Lm-oY-j6fKS8iqIvN_DG6e)
- [Node.js Event Loop - Jake Archibald](https://www.youtube.com/watch?v=cCOL7MC4Pl0)
- [Streams Handbook](https://www.youtube.com/playlist?list=PL0CCC6BD6AFF097B1)

## Best Free Course
- **Udemy**: "The Complete Node.js Developer Course" (Free sections)
- **YouTube**: Node.js Crash Course - Traversy Media
- **freeCodeCamp**: Node.js & Express Full Course

## Best Paid Course
- **Udemy**: "Advanced Node.js - Scaling Applications" - Anthony Alicea (~$15)
- **Pluralsight**: "Node.js: Advanced Concepts" - Anthony Alicea
- **Frontend Masters**: "Production Node.js" - Will Sentance

## Best Book
- **"Node.js Design Patterns"** - Mario S. Casella, Luciano Mammino
- **"Async Patterns in Node.js"** - Doug Wilson
- **"The Node.js Way"** - Felix Geisendörfer

## Blogs
- [Node.js Blog](https://nodejs.org/en/blog/)
- [Event Loop Explained - JavaScript Visualized](https://dev.to/uidotdev/javascript-visualized-event-loop-3dif)
- [Understanding Streams](https://nodesource.com/blog/understanding-streams-in-nodejs/)
- [Cluster Module Deep Dive](https://blog.risingstack.com/node-js-cluster-module-deep-dive/)

## Interview Questions

### Beginner
1. What is the Node.js event loop and why is it important?
2. Difference between `setTimeout()` and `setImmediate()`?
3. What are streams and why are they useful?
4. Explain buffers in Node.js
5. What is the difference between `process.nextTick()` and `setImmediate()`?

### Intermediate
1. How does the event loop handle promises vs callbacks?
2. Explain the phases of the Node.js event loop
3. How do streams save memory compared to loading entire files?
4. Difference between `spawn()`, `exec()`, and `fork()`?
5. What is IPC in Node.js?

### Advanced
1. How would you prevent event loop blocking in a CPU-intensive application?
2. Explain the backpressure mechanism in streams
3. When would you use worker threads vs child processes?
4. How does clustering improve application performance?
5. Design a system that processes millions of rows from a CSV file efficiently

## Mini Revision
- Event loop: 5 phases in detail
- Stream.pipe() vs manual event listeners
- Buffer memory management
- Child process communication patterns
- Cluster load balancing strategies

## Projects

### Project 1: Log Analyzer
**Objective**: Build a CLI tool that analyzes large log files using streams

**Requirements**:
- Read large log files without loading entire file in memory
- Parse and filter logs by date, level, or pattern
- Generate statistics and reports
- Support multiple output formats (JSON, CSV, plain text)
- Performance: Handle files > 1GB

**Tech Stack**: Node.js Streams, Commander.js, Chalk

**Deliverables**:
- CLI tool with multiple commands
- Unit tests for parsing logic
- Performance benchmarks

### Project 2: CLI Application
**Objective**: Create a practical CLI tool (Task Manager/File Organizer)

**Requirements**:
- User-friendly command-line interface
- Persistent data storage (JSON/SQLite)
- Multiple commands (add, list, delete, update)
- Input validation and error handling
- Help documentation

**Tech Stack**: Node.js, Commander.js, Inquirer.js

**Deliverables**:
- Fully functional CLI tool
- Documentation with usage examples
- Installation and setup guide

### Project 3: Node File Manager
**Objective**: Build a file manager with advanced operations

**Requirements**:
- List, create, read, update, delete files
- Move and copy operations
- Recursive directory operations
- File watching for changes
- Size calculations and statistics
- RESTful API with Express

**Tech Stack**: Node.js, Express, File System API

**Deliverables**:
- REST API with full CRUD
- Frontend dashboard (optional)
- Comprehensive API documentation

## Stretch Projects
1. **Build a streaming video processor** - Process video files using ffmpeg
2. **Create a real-time log monitor** - Monitor multiple log files with websockets
3. **Implement a multi-process load balancer** - Load balance requests across processes
4. **Build a worker pool system** - Manage multiple worker threads with job queues
5. **Create a streaming database backup tool** - Backup large databases efficiently

## Weekly Checklist
- [ ] Understand event loop completely
- [ ] Create at least 3 working stream examples
- [ ] Write buffer manipulation code
- [ ] Practice child process communication
- [ ] Set up and test a clustered application
- [ ] Complete all 3 projects
- [ ] Review 10+ interview questions
- [ ] Optimize an existing Node app using event loop knowledge
- [ ] Write stream tests
- [ ] Document findings and create cheat sheet

---

**Navigation**:
- [← Week 10](../weeks/Week-10.md)
- [Week 12 →](../weeks/Week-12.md)
- [Back to Roadmap](../README.md)
