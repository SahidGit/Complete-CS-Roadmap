# MongoDB & Mongoose Reference Guide

MongoDB is a document-based NoSQL database designed for high scalability and flexibility. Mongoose is an Object Data Modeling (ODM) library for MongoDB and Node.js that provides a schema-based solution to model application data.

---

## 1. Mongoose Schema and Validation

Unlike traditional SQL databases, MongoDB does not enforce structure by default. Mongoose allows you to define a structured schema, strict types, and validation rules at the application layer.

```javascript
const mongoose = require('mongoose');

const productSchema = new mongoose.Schema({
  name: {
    type: String,
    required: [true, 'Product name is required'],
    trim: true,
    maxlength: [100, 'Name cannot exceed 100 characters']
  },
  price: {
    type: Number,
    required: [true, 'Price is required'],
    min: [0, 'Price cannot be negative']
  },
  category: {
    type: String,
    enum: {
      values: ['Electronics', 'Books', 'Clothing', 'Other'],
      message: '{VALUE} is not a valid category'
    }
  },
  inStock: {
    type: Boolean,
    default: true
  },
  tags: [String] // Array of strings
}, {
  timestamps: true // Automatically adds createdAt and updatedAt fields
});

const Product = mongoose.model('Product', productSchema);
module.exports = Product;
```

---

## 2. CRUD Operations (Create, Read, Update, Delete)

### Create
```javascript
const createProduct = async () => {
  const newProduct = new Product({
    name: 'Wireless Keyboard',
    price: 49.99,
    category: 'Electronics',
    tags: ['utility', 'office']
  });
  
  await newProduct.save(); // Saves doc to MongoDB
};
```

### Read
```javascript
const findProducts = async () => {
  // Find products matching criteria, sorting price descending, selecting specific fields
  const products = await Product.find({ category: 'Electronics', price: { $gte: 20 } })
    .sort({ price: -1 })
    .select('name price') // Projection: return only name and price
    .limit(10);
};
```

### Update
Always use specialized update operators like `$set` or `$push`. Set `runValidators: true` to ensure updating records validation checks still apply.
```javascript
const updateProduct = async (id) => {
  const updatedProduct = await Product.findByIdAndUpdate(
    id,
    { $set: { price: 39.99 }, $push: { tags: 'sale' } },
    { new: true, runValidators: true } // returns the modified document, not the original
  );
};
```

### Delete
```javascript
const deleteProduct = async (id) => {
  await Product.findByIdAndDelete(id);
};
```

---

## 3. Mongoose Middleware (Hooks)

Middleware (also called pre and post hooks) are functions which are passed control during execution of asynchronous Mongoose actions.

### Pre-Save Hook (Hashing Passwords)
```javascript
const bcrypt = require('bcryptjs');

const userSchema = new mongoose.Schema({
  username: String,
  password: { type: String, required: true }
});

// Run this function BEFORE saving a user document
userSchema.pre('save', async function (next) {
  // Only hash password if it was modified (or is new)
  if (!this.isModified('password')) return next();
  
  const salt = await bcrypt.genSalt(10);
  this.password = await bcrypt.hash(this.password, salt);
  next();
});
```

---

## 4. Modeling Document Relationships

### Reference / Normalized Pattern (Similar to Foreign Keys)
Good for large, unbound collections or highly dynamic records. Use `.populate()` to fetch referenced documents during queries.

```javascript
// Post Schema
const postSchema = new mongoose.Schema({
  title: String,
  content: String,
  author: {
    type: mongoose.Schema.Types.ObjectId,
    ref: 'User', // Links to User Model
    required: true
  }
});

// Querying and Populating
const getPostDetails = async (postId) => {
  const post = await Post.findById(postId).populate('author', 'username email');
  // Returns: { title: "...", author: { _id: "...", username: "Sahid", email: "..." } }
};
```

### Embedded / Denormalized Pattern
Good for small, static datasets (e.g., subdocuments, addresses) that are always queried together with the parent document.

```javascript
const addressSchema = new mongoose.Schema({
  city: String,
  zipCode: String
});

const userSchema = new mongoose.Schema({
  name: String,
  addresses: [addressSchema] // Embedded subdocument array
});
```

---

## 5. Aggregation Framework
Used for running complex data calculations and queries (similar to SQL `GROUP BY`).

```javascript
const getCategoryMetrics = async () => {
  const stats = await Product.aggregate([
    // Stage 1: Filter products in stock
    { $match: { inStock: true } },
    // Stage 2: Group by category and calculate metrics
    {
      $group: {
        _id: '$category',
        avgPrice: { $avg: '$price' },
        totalStock: { $sum: 1 }
      }
    },
    // Stage 3: Sort by average price descending
    { $sort: { avgPrice: -1 } }
  ]);
};
```

---

## 6. Official Resources
- [MongoDB Manual Guide](https://www.mongodb.com/docs/manual/)
- [Mongoose Guide Docs](https://mongoosejs.com/docs/guide.html)
- [MongoDB Aggregation Guide](https://www.mongodb.com/docs/manual/aggregation/)
