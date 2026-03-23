# OWASP API Security Top 10 - API9: Improper Inventory Management

## 🧠 Overview
API9: Improper Inventory Management is a critical vulnerability that arises when organizations:

> ❗ Do not know all the APIs they have  
> ❗ Or fail to properly manage and control them  

This is not just a technical issue — it is also an **organizational and governance problem**.

---

## 💡 Core Concept

The core question is simple:

> 👉 Do you know all your APIs?  
> 👉 And if you do… are you actually controlling them?

---

## 📌 The Problem Has Two Parts

### 1️⃣ Awareness

Do you know:

- How many APIs exist?
- Where they are located?
- Who created them?

---

### ⚠️ The Reality

Many organizations have:

> 👻 Hidden or forgotten APIs

---

### 2️⃣ Control

Even if you know your APIs, you must ask:

- Is this API still in use?
- Does it contain vulnerabilities?
- Should it be retired?
- Is it updated?

---

## 👻 Dangerous Types of APIs

### 🧟 Zombie APIs
- Old APIs  
- No longer used  
- Still active and exposed  

---

### 👤 Shadow APIs
- Created without security team knowledge  
- Often developed individually by developers  

---

### 🔢 Old API Versions

Example:


/api/v3


Attackers will try:


/api/v2
/api/v1


> 💥 Older versions are often less secure

---

## 💣 Real-World Example: Optus Data Breach

### 📌 What Happened?

An engineer:

- Created an API  
- Exposed it to the internet ❌  
- No authentication ❌  
- Contained sensitive data ❌  

---

### 😱 Impact

> 💥 Data of **9.8 million users leaked**

Including:

- Names  
- Addresses  
- Dates of birth  
- ID/license numbers  

---

### ⚠️ How Was It Exploited?

- API was publicly accessible  
- No authentication required  
- Used **incremental IDs**

---

### 🧨 Attack Method

The attacker simply did:


ID = 1 → 2 → 3 → 4 ...


> 💥 Extracted all user data sequentially

---

## 🧠 Key Lesson

> ❌ The issue was NOT a complex hack  
> ✅ The issue was: "An API nobody was managing"

---

## 🛡️ Mitigation Strategies

### ✔️ 1. Strong API Governance

- No API should be published without:
  - Approval  
  - Security review  

---

### ✔️ 2. API Discovery (Very Important)

Ways to discover APIs:

- 🔍 Monitor traffic  
- 🧾 Analyze requests/logs  
- 🧑‍💻 Scan source code repositories  
- 🕷️ Crawl applications  
- 💣 Brute-force common API paths  

---

### 👨‍💻 Pro Tip

> 👉 Ask the development team directly

---

### ✔️ 3. Use an API Gateway

- Centralized control point  
- Monitoring + logging + protection  

---

### ✔️ 4. Remove Old APIs

- Disable outdated versions (v1, v2)  
- Force clients to upgrade  

---

### ✔️ 5. Continuous Auditing

Regularly check:

- Who has access?  
- Are there unknown APIs?  
- Are all APIs secured?  

---

## 🔑 Core Takeaway

> 🔥 "If you don't know what you have, you cannot protect it"

---

## 🎯 Simple Illustration

Imagine:

- 10 known APIs  
- 5 hidden APIs  

---

Attackers will NOT target the 10 secure ones…

> 😈 They will look for the 5 hidden, forgotten APIs

---

## 🧠 Professional Mindset

A beginner secures what is visible.

A professional asks:

> 😈 "What APIs exist that nobody is watching?"

---

## 🔥 Summary

- ✔️ Vulnerability: Poor API inventory management  
- ✔️ Cause: Lack of visibility and control  
- ✔️ Risk: Exposure of forgotten or unsecured APIs  
- ✔️ Defense: Discovery, governance, monitoring, and cleanup  

---
