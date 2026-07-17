# MongoDB & Mongoose Cheat Sheet

Quick guide for Mongoose models, validation, and standard CRUD operations.

## Database Integration (Mongoose)

### 1. Schema & Model Setup
```javascript
const mongoose = require('mongoose');

const userSchema = new mongoose.Schema({
  username: { type: String, required: true, unique: true, trim: true },
  email: { type: String, required: true, lowercase: true },
  createdAt: { type: Date, default: Date.now }
});

const User = mongoose.model('User', userSchema);
```

### 2. Secure CRUD Queries
```javascript
// Create
const newUser = await User.create({ username: 'Sahid', email: 'sahid@example.com' });

// Read (Find with projections)
const users = await User.find({ email: /example/ }).select('-__v');

// Update (Using Mongoose operators)
const updatedUser = await User.findOneAndUpdate(
  { username: 'Sahid' },
  { $set: { email: 'new-email@example.com' } },
  { new: true, runValidators: true } // Return updated doc & run validations
);
```

---

## ⚠️ Destructive Commands (Use with Caution)

> [!CAUTION]
> Aggressive delete queries or index rebuilds can wipe out records or degrade production database performance.

### 1. Dropping Databases and Collections
```javascript
// Drop the database entirely
await mongoose.connection.db.dropDatabase();

// Clear an entire collection
await User.deleteMany({});
```
*Why it's dangerous:* Running these commands in production will result in immediate, non-recoverable data loss unless backups are configured.

---

## Authoritative Documentation
- [MongoDB Official Documentation](https://www.mongodb.com/docs/)
- [Mongoose Official Documentation](https://mongoosejs.com/docs/)
