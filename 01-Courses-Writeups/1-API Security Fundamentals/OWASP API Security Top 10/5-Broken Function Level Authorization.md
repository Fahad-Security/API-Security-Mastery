# OWASP API Security Top 10 - API5: Broken Function Level Authorization

## 🧠 Overview
API5: Broken Function Level Authorization is a critical vulnerability that occurs when an API fails to properly restrict **which actions (functions)** a user is allowed to perform.

Unlike other vulnerabilities that focus on *data access*, this issue is about:

> ❗ What operations a user can execute.

---

## 📌 Core Concept

The system allows users to perform actions they **should NOT be authorized to perform**.

> ❗ The problem is not "what data you can access"  
> ❗ The problem is "what actions you can execute"

---

## 🔥 Simple Example

Consider the following API:


GET /api/account


✔️ This is normal — it retrieves account data.

---

Now consider:


POST /api/account/upgrade


❗ This endpoint is supposed to be used only by the backend system.

But if a normal user can access it:

> 💥 They can upgrade their account from **free → premium** without paying 💰

---

## 🚨 Real-World Example: Bumble API

### What Happened?

The application exposed:

1. Endpoint to view account type:

GET /api/account


2. Endpoint to modify account type:

POST /api/account


---

### The Problem

❗ There was **no proper authorization check**

---

### The Result

> 💥 Any user could upgrade their account to premium for free

---

## 🧠 Important Distinction (Very Important)

| Vulnerability Type | Description |
|-------------------|------------|
| 🔴 BOLA           | Accessing other users' data |
| 🔵 BOPLA          | Modifying properties inside an object |
| 🟢 Function Level Authorization (This) | Executing unauthorized actions |

---

## 🎯 Clear Example

Normal behavior:


GET /api/invoices


Dangerous behavior:


DELETE /api/invoices/123


❗ If any user can delete invoices:

> 💥 This is a critical vulnerability

---

## ⚠️ High-Risk Scenarios

If authorization is broken, attackers may:

- Reset other users' passwords
- Delete critical data
- Modify balances
- Transfer money
- Grant themselves admin privileges

---

## 🧠 Attacker Mindset

Instead of asking:

> "Can I see this data?"

Ask:

> 😈 "Can I perform an action I shouldn't be allowed to?"

---

## 🔍 Signs of Vulnerability

### 1️⃣ Multiple HTTP Methods

- GET
- POST
- PUT
- DELETE

Different methods may expose hidden functionality.

---

### 2️⃣ Sensitive Endpoints

Look for:

- `/api/admin`
- `/api/delete`
- `/api/update`
- `/api/upgrade`

---

## 🛠️ How to Test This Vulnerability

### Step 1: Intercept Requests

Use tools like:

- Burp Suite

---

### Step 2: Modify HTTP Methods

Try changing:

- `GET → POST`
- `GET → DELETE`

---

### Step 3: Discover Hidden Endpoints

Test endpoints such as:


/api/admin
/api/user/delete
/api/account/upgrade


---

### Step 4: Test Without Proper Privileges

- Use a normal user account
- Attempt to access admin-level functionality

---

## 🔥 Practical Example

Normal request:


GET /api/user/profile


---

Try:


DELETE /api/user/123


---

### 🚨 Red Flag

If the request succeeds:

> 💥 You have discovered a critical vulnerability

---

## 🧠 Professional Thinking

A beginner focuses on visible features.

A professional asks:

> 😈 "What hidden operations exist that are not exposed in the UI?"

---

## 💡 Key Lesson

> ❗ Never trust that "users cannot see a button"

Because:

> 🚨 Attackers do NOT rely on the UI at all  
> They interact directly with the API

---

## 🚀 Hands-On Practice

To master this vulnerability:

1. Choose a target (lab or authorized scope)
2. Analyze API traffic
3. Look for:
   - `update`
   - `delete`
   - `admin`
4. Try executing them manually

---

## 🔥 Summary

- ✔️ Vulnerability: Broken function-level authorization  
- ✔️ Attack: Execute unauthorized actions  
- ✔️ Goal: Gain control over system functionality  

---

## 🎯 Quick Comparison (Important)

| Type | What is Broken? | Example |
|------|----------------|--------|
| BOLA | Object access | Access another user's data |
| BOPLA | Object properties | Modify hidden fields |
| Function Level Auth | Actions/Functions | Delete, upgrade, admin actions |

---
