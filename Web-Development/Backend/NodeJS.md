# Node.js Reference Guide

Node.js is a cross-platform, open-source JavaScript runtime environment that executes JavaScript code outside a web browser, built on Chrome's V8 JavaScript engine.

---

## 1. Node.js Architecture

### The Event Loop & libuv
Node.js uses a single-threaded event loop architecture to handle asynchronous I/O operations. While JavaScript runs on a single main thread, the underlying C++ library **libuv** handles system tasks (file I/O, networking) using a multi-threaded system thread pool.

```
┌───────────────────────────┐
│       Incoming Requests    │
└─────────────┬─────────────┘
              ▼
┌───────────────────────────┐
│        Event Loop         │ ◄─── (Single-threaded)
└─────────────┬─────────────┘
              ├──────────────────────────┐
              ▼                          ▼
   Non-blocking I/O tasks       Blocking OS-level tasks
   (Network, DNS, etc.)         (File System, Crypto)
              │                          │
              ▼                          ▼
    Handled by Kernel             Thread Pool (libuv)
```

### Event Loop Phases
1. **Timers**: Executes callbacks scheduled by `setTimeout()` and `setInterval()`.
2. **Pending Callbacks**: Executes I/O callbacks deferred from the previous loop iteration.
3. **Idle, Prepare**: Used only internally.
4. **Poll**: Retrieves new I/O events; executes I/O related callbacks.
5. **Check**: Executes `setImmediate()` callbacks.
6. **Close Callbacks**: Executes close events (e.g., `socket.on('close')`).

*Note:* `process.nextTick()` and microtasks (promises) are executed immediately after the current operation finishes, before the event loop transitions to the next phase.

---

## 2. Core Modules

### File System (`fs/promises`)
Always prefer the promise-based API over synchronous methods or error-first callbacks.

```javascript
const fs = require('fs/promises');
const path = require('path');

async function manageFiles() {
  const filePath = path.join(__dirname, 'data.txt');
  
  try {
    // Write File
    await fs.writeFile(filePath, 'Hello, Node.js!', 'utf-8');
    
    // Read File
    const content = await fs.readFile(filePath, 'utf-8');
    console.log(content);
    
    // Append File
    await fs.appendFile(filePath, '\nNew line appended.');
  } catch (err) {
    console.error('File operation failed:', err);
  }
}
```

### Path Module (`path`)
Always use the `path` module instead of string concatenation to handle file paths across different operating systems (Windows uses `\`, Posix uses `/`).

```javascript
const path = require('path');

// Join multiple segments
const fullPath = path.join('/usr', 'local', 'bin'); // '/usr/local/bin'

// Resolve relative paths into absolute paths
const absolutePath = path.resolve('src', 'components'); // 'C:\Users\...\src\components'

// Extract file extensions or base names
console.log(path.extname('server.js')); // '.js'
console.log(path.basename('/src/index.html')); // 'index.html'
```

### HTTP Module (`http`)
Creating a low-level HTTP server without frameworks.

```javascript
const http = require('http');

const server = http.createServer((req, res) => {
  if (req.method === 'GET' && req.url === '/api/health') {
    res.writeHead(200, { 'Content-Type': 'application/json' });
    res.end(JSON.stringify({ status: 'UP', timestamp: new Date() }));
  } else {
    res.writeHead(404, { 'Content-Type': 'text/plain' });
    res.end('Not Found');
  }
});

server.listen(3000, () => console.log('Server running on port 3000'));
```

---

## 3. Module Systems

### CommonJS (CJS) vs. ES Modules (ESM)

| Feature | CommonJS (CJS) | ES Modules (ESM) |
| :--- | :--- | :--- |
| **Syntax** | `require()` & `module.exports` | `import` & `export` |
| **Loading** | Synchronous, dynamic | Asynchronous, static |
| **Filename** | Defaults in `.js` | Enabled via `"type": "module"` in `package.json` or `.mjs` |
| **Globals** | Has `__dirname`, `__filename` | No `__dirname` (must construct via `import.meta.url`) |

#### CommonJS Format:
```javascript
// math.js
const add = (a, b) => a + b;
module.exports = { add };

// server.js
const { add } = require('./math');
```

#### ES Modules Format:
```javascript
// math.mjs
export const add = (a, b) => a + b;

// server.mjs
import { add } from './math.mjs';

// Re-creating __dirname in ESM:
import { fileURLToPath } from 'url';
import { dirname } from 'path';
const __filename = fileURLToPath(import.meta.url);
const __dirname = dirname(__filename);
```

---

## 4. Node.js Globals and Utilities

### Process Object (`process`)
Useful for reading environment variables and interacting with the system process.
```javascript
// Load environment variables (e.g., from a .env file)
const port = process.env.PORT || 8080;
const nodeEnv = process.env.NODE_ENV;

// Exiting process gracefully
if (!process.env.DATABASE_URL) {
  console.error('Fatal Error: DATABASE_URL is not defined.');
  process.exit(1); // Exit code 1 indicates failure
}
```

### Buffers & Streams
Buffers represent fixed-size, raw memory allocations outside the V8 heap. Streams allow reading or writing data chunk-by-chunk instead of loading the entire file into memory (preventing heap overflows).

```javascript
const fs = require('fs');

const readStream = fs.createReadStream('./huge-log.txt', 'utf-8');
const writeStream = fs.createWriteStream('./compressed-backup.txt');

// Pipe reads to writes dynamically (non-blocking chunk streaming)
readStream.pipe(writeStream);

readStream.on('error', (err) => console.error('Streaming error:', err));
```

---

## 5. Official Resources
- [Node.js Official Documentation](https://nodejs.org/docs/latest/api/)
- [Node.js Guides & Tutorials](https://nodejs.org/en/docs/guides)
