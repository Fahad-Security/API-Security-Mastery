# OWASP API Security Top 10 - API10: Unsafe Consumption of APIs

## 🧠 Overview
API10: Unsafe Consumption of APIs focuses on a critical but often overlooked risk:

> ❗ Using external (third-party) APIs in an insecure way

In previous topics, the focus was on securing **your own APIs**.  
Here, the focus shifts to:

> 👉 How to protect your system when consuming APIs from other providers

---

## 💡 Core Concept

Modern applications rely heavily on external APIs, such as:

- Payment services  
- Authentication providers  
- Maps and location services  
- Email and messaging APIs  

---

### ❌ Common Mistake

> "This is a big company → their API must be secure"

✔️ This assumption is **completely wrong**

---

## ⚠️ Where is the Risk?

There are two main risks:

### 1️⃣ The External API Itself May Be Vulnerable
- The provider may have security flaws  

---

### 2️⃣ You May Be Using It Incorrectly
- Improper integration introduces vulnerabilities  

---

> 💥 In both cases… **you are the one affected**

---

## 💣 Real-World Example: Companies House (UK)

### 📌 What Happened?

A user registered a company name containing **JavaScript code (XSS payload)**:


">


---

### 😱 The Problem

- The system stored the input as-is  
- When displayed → the script executed  

---

### 💥 Impact

Any application consuming this data:

- Could execute malicious JavaScript  
- Could expose users to XSS attacks  

---

## 🧠 Critical Insight

> 👉 The attack did NOT target your application directly  
> 👉 It targeted an external API… but you became vulnerable

---

## ⚠️ Why This is Dangerous

If you trust external API data blindly:

- 💥 XSS attacks  
- 💥 Session hijacking  
- 💥 Account compromise  

---

## 🔥 Golden Rule

> ❗ Never trust any external API  
> Even if it belongs to a large company

---

## 🛡️ Mitigation Strategies

### ✔️ 1. Inventory External APIs

- Know every third-party API you use  
- Document them clearly  

---

### ✔️ 2. Do NOT Trust Third-Party Data

- Always validate input  
- Never render data directly to users  

---

### ✔️ 3. Apply Internal Security Standards

Treat external APIs like your own:

- Validate inputs  
- Enforce authorization  
- Prevent data leakage  

---

### ✔️ 4. Assess API Security

- Request:
  - Penetration testing reports  
  - Security documentation  

- Or test them yourself (if permitted)

---

### ✔️ 5. Secure Integration (Very Important)

Most vulnerabilities come from:

> ❗ How you integrate the API, not the API itself

---

## 🎯 Simple Example

### Vulnerable Scenario

- External API returns a username  
- Username contains JavaScript  

If rendered directly:

> 💥 XSS executed

---

### Secure Scenario

- Validate and sanitize the data  

> ✅ Safe rendering

---

## 🧠 Professional Mindset

A beginner thinks:

> "This API is trusted"

A professional thinks:

> 😈 "What if this API is compromised?"

---

## 🔥 Final Summary of OWASP API Top 10

| # | Concept |
|---|--------|
| API1 | Broken Object Level Authorization |
| API2 | Broken Authentication |
| API3 | Broken Object Property Level Authorization |
| API4 | Unrestricted Resource Consumption |
| API5 | Broken Function Level Authorization |
| API6 | Business Logic Abuse |
| API7 | SSRF |
| API8 | Security Misconfiguration |
| API9 | Improper Inventory Management |
| API10 | Unsafe Consumption of APIs |

---

## 🔑 Final Takeaway

> 🔥 "Security is not only about what you build…  
> but also about what you trust"

---
