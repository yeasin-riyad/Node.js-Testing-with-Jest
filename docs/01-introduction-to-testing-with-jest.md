# Node.js Testing with Jest

## 📖 Introduction

Node.js অ্যাপ্লিকেশন তৈরি করার সময় শুধুমাত্র কোড লেখা যথেষ্ট নয়। একজন দক্ষ Backend Developer-এর জন্য নিশ্চিত করতে হয় যে লেখা কোডটি সঠিকভাবে কাজ করছে, ভবিষ্যতে নতুন পরিবর্তনের ফলে পুরোনো ফিচার নষ্ট হচ্ছে না এবং Production-এ যাওয়ার আগে সম্ভাব্য Bug গুলো ধরা পড়ছে।

এই কাজটিই সহজ করে **Testing**।

Node.js ইকোসিস্টেমে **Jest** হলো সবচেয়ে জনপ্রিয় এবং শক্তিশালী JavaScript Testing Framework-গুলোর একটি। এটি Meta (Facebook) কর্তৃক তৈরি এবং বর্তমানে Node.js, Express.js, NestJS, React, Next.js এবং TypeScript প্রজেক্টে ব্যাপকভাবে ব্যবহৃত হয়।

এই ডকুমেন্টেশন সিরিজে আমরা শুরু থেকে Professional Level পর্যন্ত **Node.js Testing with Jest** শিখব।

---

# 🎯 What is Node.js Testing?

Node.js Testing হলো আপনার Node.js অ্যাপ্লিকেশনের বিভিন্ন অংশ (Function, API, Database Logic, Middleware ইত্যাদি) স্বয়ংক্রিয়ভাবে পরীক্ষা করার প্রক্রিয়া।

অর্থাৎ, আপনি আগে থেকেই কিছু **Test Case** লিখে রাখবেন, যা পরবর্তীতে আপনার কোড প্রত্যাশিত ফলাফল দিচ্ছে কিনা তা যাচাই করবে।

সহজভাবে বলতে গেলে—

> **Testing হলো আপনার কোড সঠিকভাবে কাজ করছে কিনা তা প্রোগ্রাম দিয়েই আবার পরীক্ষা করা।**

---

# 🧪 What is Jest?

**Jest** হলো একটি JavaScript Testing Framework যা Meta (Facebook) তৈরি করেছে।

এটি Developer-দের দ্রুত, সহজ এবং নির্ভরযোগ্যভাবে Test লেখার সুযোগ দেয়।

Jest-এর মাধ্যমে আপনি সহজেই Test লিখতে, Run করতে এবং Bug খুঁজে বের করতে পারবেন।

---

# 🤔 Why Do We Need Testing?

ধরুন আপনি একটি Calculator Function লিখেছেন।

```javascript
function add(a, b) {
  return a + b;
}
```

আপনি আশা করছেন—

```javascript
add(5, 3);
```

Output হবে—

```text
8
```

কিন্তু ভুলবশত যদি লিখে ফেলেন—

```javascript
function add(a, b) {
  return a - b;
}
```

এখন Function টি ভুল Result দেবে।

যদি Testing না থাকে, তাহলে এই Bug Production পর্যন্ত চলে যেতে পারে।

কিন্তু Jest-এর Test থাকলে সাথে সাথেই জানিয়ে দেবে যে Function টি ভুল Result দিচ্ছে।

---

# 💡 Why Choose Jest?

Jest জনপ্রিয় হওয়ার প্রধান কারণগুলো হলো—

- ✅ Zero Configuration
- ✅ Easy Setup
- ✅ Very Fast
- ✅ Excellent Error Messages
- ✅ Built-in Mocking
- ✅ Snapshot Testing
- ✅ Code Coverage
- ✅ Watch Mode
- ✅ TypeScript Support
- ✅ Large Community

---

# ⚙️ What Can Jest Test?

Jest ব্যবহার করে আপনি বিভিন্ন ধরনের Testing করতে পারবেন।

### Function Testing

```javascript
function multiply(a, b) {
  return a * b;
}
```

---

### API Testing

- GET API
- POST API
- PUT API
- DELETE API

---

### Authentication Testing

- Login
- Register
- JWT
- Password Hashing

---

### Database Logic Testing

- Create User
- Update User
- Delete User
- Query Validation

---

### Middleware Testing

- Authentication Middleware
- Authorization Middleware
- Validation Middleware

---

### Utility Function Testing

- Slug Generator
- Date Formatter
- Pagination
- Helper Functions

---

# 📚 Types of Testing

Testing-এর অনেক ধরন রয়েছে। Jest দিয়ে এর বেশিরভাগই করা যায়।

## Unit Testing

একটি ছোট Function বা Component আলাদাভাবে Test করা।

Example:

```javascript
add(5, 3);
```

---

## Integration Testing

একাধিক Module একসাথে ঠিকভাবে কাজ করছে কিনা তা পরীক্ষা করা।

Example:

```
Route
   ↓
Controller
   ↓
Service
   ↓
Database
```

---

## API Testing

API Request এবং Response সঠিক কিনা তা পরীক্ষা করা।

Example:

```
POST /login

GET /users
```

---

## Snapshot Testing

UI বা Response পূর্বের Snapshot-এর সাথে মিলছে কিনা তা পরীক্ষা করা।

---

# 📝 Manual Testing vs Automated Testing

## Manual Testing

Developer নিজে Test করে।

```javascript
console.log(add(5, 3));
```

Output দেখে নিশ্চিত হয়।

এটি সময়সাপেক্ষ এবং বড় Project-এর জন্য কার্যকর নয়।

---

## Automated Testing

একবার Test লিখে রাখলে—

```bash
npm test
```

Run করলেই হাজার হাজার Test কয়েক সেকেন্ডে সম্পন্ন হয়ে যায়।

---

# 🧪 Simple Jest Example

ধরুন একটি Function আছে।

```javascript
function add(a, b) {
  return a + b;
}
```

এর Test হতে পারে—

```javascript
test("adds 2 + 3 = 5", () => {
  expect(add(2, 3)).toBe(5);
});
```

এখানে—

- `test()` → একটি Test Case তৈরি করে
- `expect()` → Expected Result নির্ধারণ করে
- `toBe()` → Exact Value Compare করে

---

# ❌ What Happens If a Test Fails?

ধরুন Function টি ভুল Result দিচ্ছে।

```javascript
function add(a, b) {
  return a - b;
}
```

তাহলে Test Run করলে Jest দেখাবে—

```text
Expected: 5

Received: -1
```

ফলে খুব সহজেই Bug খুঁজে পাওয়া যায়।

---

# 🏗️ Typical Project Structure

```
project/

src/
    controllers/
    services/
    routes/
    middleware/
    utils/

tests/
    auth.test.js
    user.test.js
    product.test.js
```

অথবা—

```
src/

controllers/
services/

__tests__/
```

---

# 🚀 Benefits of Learning Jest

Jest শেখার মাধ্যমে আপনি—

- Bug দ্রুত খুঁজে বের করতে পারবেন।
- Refactoring নিরাপদভাবে করতে পারবেন।
- Production Bug কমাতে পারবেন।
- Code Quality বৃদ্ধি করতে পারবেন।
- Team Collaboration সহজ হবে।
- CI/CD Pipeline-এ Automated Test চালাতে পারবেন।
- Professional Backend Developer হিসেবে কাজ করার দক্ষতা অর্জন করবেন।

---

# 📅 What You Will Learn in This Course

এই ডকুমেন্টেশন সিরিজে আমরা নিচের বিষয়গুলো শিখব।

1. Introduction to Testing
2. Jest Installation & Project Setup
3. Writing Your First Test
4. Test Suites
5. Test Cases
6. Matchers
7. Testing Functions
8. Testing Async Code
9. Mock Functions
10. Mock Modules
11. API Testing with Supertest
12. Database Testing
13. Code Coverage
14. Snapshot Testing
15. Test-Driven Development (TDD)
16. Best Practices
17. Testing Real-World Node.js Applications

---

# 🎯 Prerequisites

এই সিরিজ শুরু করার আগে নিচের বিষয়গুলোর বেসিক ধারণা থাকলে ভালো হবে।

- JavaScript (ES6+)
- Node.js
- npm
- Modules
- Async/Await
- Express.js (Recommended)

---

# 🎯 Learning Outcome

এই সিরিজ শেষ করার পর আপনি—

- Jest দিয়ে Professional Testing লিখতে পারবেন।
- Node.js Backend-এর Function Test করতে পারবেন।
- Express API Test করতে পারবেন।
- Mocking করতে পারবেন।
- Database Testing করতে পারবেন।
- Coverage Report তৈরি করতে পারবেন।
- Production Ready Testing Strategy তৈরি করতে পারবেন।
- Real-world Backend Project-এর জন্য Automated Test লিখতে পারবেন।

---

# 📚 Recommended Learning Order

```
01 - Introduction to Testing with Jest
        ↓
02 - Installation & Project Setup
        ↓
03 - Writing Your First Test
        ↓
04 - Test Suites & Test Cases
        ↓
05 - Matchers
        ↓
06 - Testing Functions
        ↓
07 - Async Testing
        ↓
08 - Mocking
        ↓
09 - API Testing
        ↓
10 - Database Testing
        ↓
11 - Advanced Jest
        ↓
12 - Best Practices
```

---

# 📌 Conclusion

Testing হলো আধুনিক সফটওয়্যার ডেভেলপমেন্টের একটি অপরিহার্য অংশ। Jest ব্যবহার করে আমরা সহজেই Node.js অ্যাপ্লিকেশনের বিভিন্ন অংশ স্বয়ংক্রিয়ভাবে পরীক্ষা করতে পারি। এর মাধ্যমে Bug দ্রুত শনাক্ত করা যায়, Code-এর মান বৃদ্ধি পায় এবং বড় প্রজেক্টে নিরাপদভাবে নতুন Feature যোগ করা সম্ভব হয়।

এই ডকুমেন্টেশন সিরিজে আমরা ধাপে ধাপে Jest-এর প্রতিটি গুরুত্বপূর্ণ বিষয় শিখব এবং বাস্তব উদাহরণের মাধ্যমে Production-Ready Testing Strategy তৈরি করা শিখব।

---

## 🚀 Next Topic

**02 - Installing Jest & Project Setup**