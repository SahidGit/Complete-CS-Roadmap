# Express.js Reference Guide

Express.js is a minimal and flexible Node.js web application framework that provides a robust set of features for building web and mobile applications, including RESTful APIs.

---

## 1. Application Setup & Basic Routing

### Standard Express App structure
```javascript
const express = require('express');
const app = express();
const PORT = process.env.PORT || 3000;

// Enable JSON parsing middleware (built-in)
app.use(express.json());

// Basic Route
app.get('/api/health', (req, res) => {
  res.status(200).json({ status: 'healthy', code: 200 });
});

app.listen(PORT, () => {
  console.log(`Server listening on port ${PORT}`);
});
```

### Route Parameters vs. Query Parameters
- **Route Parameters**: Used for resource identification (required).
- **Query Parameters**: Used for filtering, sorting, or paginating (optional).

```javascript
// Route parameter: accessed via req.params
// Example GET request: /api/users/99
app.get('/api/users/:id', (req, res) => {
  const userId = req.params.id;
  res.status(200).json({ userId });
});

// Query parameter: accessed via req.query
// Example GET request: /api/products?category=electronics&limit=10
app.get('/api/products', (req, res) => {
  const { category, limit } = req.query;
  res.status(200).json({ category, limit });
});
```

---

## 2. Middleware Architecture

Middleware functions are functions that have access to the request object (`req`), the response object (`res`), and the next middleware function in the application’s request-response cycle (usually denoted as `next`).

```
Request ──► [ Middleware 1 ] ──► [ Middleware 2 ] ──► [ Route Handler ] ──► Response
```

### Custom Middleware Anatomy
Always execute `next()` or send a response via `res` within a middleware. Otherwise, the request will hang indefinitely.

```javascript
const loggerMiddleware = (req, res, next) => {
  console.log(`[${new Date().toISOString()}] ${req.method} ${req.url}`);
  next(); // Pass control to the next handler
};

// Apply globally to all incoming requests
app.use(loggerMiddleware);
```

### Router-Level Middleware (Grouping Routes)
Use `express.Router` to create modular, mountable route handlers.

```javascript
// routes/users.js
const express = require('express');
const router = express.Router();

router.get('/', (req, res) => res.send('User List'));
router.post('/', (req, res) => res.status(201).send('User Created'));

module.exports = router;

// server.js
const userRouter = require('./routes/users');
app.use('/api/users', userRouter); // Mount router under namespace
```

---

## 3. Advanced Error Handling

Always write a global error-handling middleware at the very end of your middleware stack (after all routes). It must accept exactly **four parameters** (`err`, `req`, `res`, `next`) for Express to identify it as an error handler.

```javascript
// Global error handling middleware
app.use((err, req, res, next) => {
  console.error(err.stack); // Log full trace locally

  const statusCode = err.statusCode || 500;
  res.status(statusCode).json({
    error: {
      message: err.message || 'Internal Server Error',
      status: statusCode,
      timestamp: new Date().toISOString()
    }
  });
});
```

### Catching Asynchronous Errors
In Express 4, asynchronous errors must be passed explicitly to `next()` to prevent crashing the thread:

```javascript
app.get('/api/data', async (req, res, next) => {
  try {
    const data = await fetchDatabaseRecord();
    res.json(data);
  } catch (error) {
    next(error); // Express passes this to the global error middleware
  }
});
```

---

## 4. API Security Best Practices

### Essential Middlewares
Always secure your Express application headers and origins.

```javascript
const cors = require('cors');
const helmet = require('helmet');
const rateLimit = require('express-rate-limit');

// 1. HTTP Header Protection
app.use(helmet()); 

// 2. CORS (Cross-Origin Resource Sharing)
app.use(cors({
  origin: process.env.CLIENT_ORIGIN || 'http://localhost:3000',
  methods: ['GET', 'POST', 'PUT', 'DELETE'],
  credentials: true
}));

// 3. API Rate Limiting (Prevents Brute-Force / DDOS)
const limiter = rateLimit({
  windowMs: 15 * 60 * 1000, // 15 minutes
  max: 100, // Limit each IP to 100 requests per window
  message: 'Too many requests from this IP, please try again later.'
});
app.use('/api/', limiter);
```

---

## 5. Official Resources
- [Express.js Official Documentation Guide](https://expressjs.com/en/guide/routing.html)
- [Express API Reference](https://expressjs.com/en/4x/api.html)
- [MDN: Express/Node Web Framework Intro](https://developer.mozilla.org/en-US/docs/Learn_web_development/Extensions/Server-side/Express_Nodejs)
