# Unit Test, Integration Test & End-to-End (E2E) Test

## 📖 Introduction

Software Testing-এর অন্যতম গুরুত্বপূর্ণ বিষয় হলো **Testing-এর বিভিন্ন ধরন (Types of Testing)** সম্পর্কে জানা। কারণ, একটি বড় Application-এর প্রতিটি অংশ একইভাবে Test করা হয় না।

ধরুন, আপনি একটি **Node.js + Express** Backend Application তৈরি করেছেন। এখানে ছোট একটি Function Test করার পদ্ধতি এবং পুরো Login System Test করার পদ্ধতি এক নয়।

এই কারণেই Testing-কে সাধারণত তিনটি প্রধান ভাগে ভাগ করা হয়—

- Unit Test
- Integration Test
- End-to-End (E2E) Test

প্রতিটি Testing-এর উদ্দেশ্য, পরিধি (Scope) এবং ব্যবহার ভিন্ন।

---

# 🎯 Overview

| Testing Type | কী Test করে? |
|--------------|--------------|
| Unit Test | একটি ছোট Function বা Logic |
| Integration Test | একাধিক Module বা Component একসাথে |
| End-to-End (E2E) Test | পুরো Application-এর User Workflow |

---

# 🧩 What is Unit Test?

Unit Test হলো Application-এর **সবচেয়ে ছোট Unit (Function, Method অথবা Class)** আলাদাভাবে Test করা।

এখানে শুধুমাত্র নির্দিষ্ট একটি Logic Test করা হয়।

Database, API কিংবা অন্য কোন Module-এর উপর নির্ভর করা হয় না।

---

## Example

```javascript
function add(a, b) {
    return a + b;
}
```

Test

```javascript
test("adds two numbers", () => {
    expect(add(5, 3)).toBe(8);
});
```

এখানে শুধুমাত্র `add()` Function Test করা হয়েছে।

---

## Another Example

```javascript
function isValidPassword(password) {
    return password.length >= 8;
}
```

এখন শুধুমাত্র Password Validation Logic Test করা হবে।

---

## What Can Be Unit Tested?

- Utility Functions
- Helper Functions
- Service Functions
- Validation Functions
- Business Logic
- Mathematical Calculations

---

## Unit Test Characteristics

✅ Tests a single Function

✅ No Database

✅ No API

✅ No External Services

✅ Very Fast

✅ Easy to Debug

---

## Example Flow

```text
Function
    │
    ▼
Unit Test
    │
    ▼
Result
```

---

# 🔗 What is Integration Test?

Integration Test হলো একাধিক Module অথবা Component একসাথে সঠিকভাবে কাজ করছে কিনা তা পরীক্ষা করা।

এখানে Application-এর বিভিন্ন Layer-এর মধ্যে Communication Test করা হয়।

---

## Example

ধরুন একটি Login API আছে।

```text
Route
   │
   ▼
Controller
   │
   ▼
Service
```

এই তিনটি Layer একসাথে Test করা হবে।

---

## Larger Example

```text
Route
   │
   ▼
Controller
   │
   ▼
Service
   │
   ▼
Database
```

এখন Database-ও যুক্ত হয়েছে।

সব Layer একসাথে ঠিকভাবে কাজ করছে কিনা সেটাই Integration Test।

---

## Example Scenario

```http
POST /users
```

Flow

```text
Request

↓

Route

↓

Controller

↓

Service

↓

Database

↓

Response (201 Created)
```

---

## What Can Be Integration Tested?

- Route + Controller
- Controller + Service
- Service + Database
- Multiple Modules
- Authentication Flow
- Database Queries

---

## Integration Test Characteristics

✅ Multiple Modules Tested Together

✅ Database May Be Used

✅ API Can Be Tested

✅ Real Communication Between Layers

---

## Example Flow

```text
Route

↓

Controller

↓

Service

↓

Database
```

---

# 🌍 What is End-to-End (E2E) Test?

End-to-End Testing (E2E) হলো পুরো Application একজন বাস্তব User যেভাবে ব্যবহার করবে সেইভাবে শুরু থেকে শেষ পর্যন্ত Test করা।

এখানে Application-এর প্রতিটি Layer কাজ করে।

---

## Example

একজন User

```text
Register

↓

Login

↓

Create Product

↓

Update Product

↓

Delete Product

↓

Logout
```

এই পুরো Workflow Test করা হবে।

---

## E-commerce Example

```text
Homepage

↓

Login

↓

Search Product

↓

Add To Cart

↓

Checkout

↓

Payment

↓

Order Success
```

এটি একটি সম্পূর্ণ End-to-End Test।

---

## Backend Example

```text
Client

↓

Express API

↓

Authentication

↓

Controller

↓

Service

↓

Database

↓

JWT

↓

Response
```

পুরো Flow বাস্তব User-এর মতো Test করা হয়।

---

## E2E Test Characteristics

✅ Entire Application Tested

✅ Real User Workflow

✅ Real API

✅ Real Authentication

✅ Database Included

✅ Highest Confidence

---

# 📊 Comparison

| Feature | Unit Test | Integration Test | End-to-End Test |
|----------|-----------|------------------|-----------------|
| Scope | Small | Medium | Large |
| Tests | Single Function | Multiple Modules | Entire Application |
| Database | ❌ | ✅ Optional | ✅ Usually |
| API | ❌ | ✅ | ✅ |
| Authentication | ❌ | ✅ | ✅ |
| Speed | ⚡ Fastest | 🚀 Medium | 🐢 Slowest |
| Complexity | Low | Medium | High |
| Debugging | Easy | Moderate | Difficult |

---

# 🎯 Real-World Example (Login API)

## Unit Test

```text
verifyPassword()

↓

true
```

শুধু Password Verification Function Test।

---

## Integration Test

```text
POST /login

↓

Controller

↓

Service

↓

Database

↓

JWT
```

API-এর বিভিন্ন Module একসাথে Test।

---

## End-to-End Test

```text
Browser

↓

Login Page

↓

API

↓

Database

↓

Dashboard
```

পুরো Login Experience Test।

---

# 🚗 Real-Life Analogy

ধরুন আপনি একটি গাড়ি তৈরি করছেন।

## Unit Test

শুধু Engine ঠিকমতো চলছে কিনা পরীক্ষা করা।

---

## Integration Test

Engine, Gear এবং Brake একসাথে কাজ করছে কিনা পরীক্ষা করা।

---

## End-to-End Test

পুরো গাড়ি চালিয়ে দেখা—

- Engine ঠিক আছে?
- Brake কাজ করছে?
- Steering ঠিক আছে?
- Gear ঠিকমতো পরিবর্তন হচ্ছে?

অর্থাৎ একজন Driver যেভাবে ব্যবহার করবে, ঠিক সেইভাবে পরীক্ষা করা।

---

# 📌 Which One Should You Use?

বাস্তব Project-এ তিনটিই গুরুত্বপূর্ণ।

### Unit Test

যখন শুধুমাত্র একটি Function Test করতে চান।

### Integration Test

যখন একাধিক Module-এর মধ্যে Communication যাচাই করতে চান।

### End-to-End Test

যখন পুরো User Journey ঠিকমতো কাজ করছে কিনা নিশ্চিত হতে চান।

---

# 💡 Best Practice

একটি ভালো Backend Project-এ সাধারণত—

- বেশি সংখ্যক **Unit Test**
- প্রয়োজনীয় **Integration Test**
- গুরুত্বপূর্ণ User Flow-এর জন্য **End-to-End Test**

লেখা হয়।

এটিকে অনেক সময় **Testing Pyramid** Approach বলা হয়।

```text
          End-to-End
        ───────────────
        Integration Test
   ─────────────────────────
         Unit Tests
────────────────────────────────
```

অর্থাৎ—

- সবচেয়ে বেশি Unit Test
- তার থেকে কম Integration Test
- সবচেয়ে কম End-to-End Test

---

# 🎯 Key Takeaways

- **Unit Test** একটি ছোট Function বা Logic Test করে।
- **Integration Test** একাধিক Module একসাথে সঠিকভাবে কাজ করছে কিনা Test করে।
- **End-to-End Test** পুরো Application একজন User-এর দৃষ্টিকোণ থেকে Test করে।
- একটি Production-Ready Application-এ এই তিন ধরনের Testing-ই গুরুত্বপূর্ণ।

---

# 📚 Summary

আধুনিক Software Development-এ শুধুমাত্র কোড লেখা যথেষ্ট নয়; সেই কোড নির্ভরযোগ্যভাবে কাজ করছে কিনা নিশ্চিত করাও সমান গুরুত্বপূর্ণ। Unit Test ছোট ছোট Logic যাচাই করে, Integration Test বিভিন্ন Module-এর সমন্বয় পরীক্ষা করে এবং End-to-End Test পুরো Application-এর বাস্তব User Workflow যাচাই করে।

একটি ভালো Testing Strategy এই তিনটি Testing-এর সঠিক সমন্বয়ের উপর নির্ভর করে।

---

## 🚀 Next Topic

**03 - Installing Jest & Project Setup**