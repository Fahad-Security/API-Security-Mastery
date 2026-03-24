# 👁️ API Security - Monitoring (Runtime Protection & Detection)

## 🧠 Overview
Monitoring in API Security focuses on:

> 👉 Observing APIs in **production (runtime)** to detect issues and attacks

---

## 🎯 Main Goal

Monitoring helps answer:

- Is the API functioning normally?  
- Is there an ongoing attack?  
- Are security controls working correctly?  

---

# 🧱 Core Components of Monitoring

---

## 1️⃣ Runtime Protection (Real-Time Defense)

### 📌 What is it?

> 👉 Protecting the API **instantly** while requests are being processed

---

### 🔒 Examples

- Enforcing authentication before access  
- Filtering requests by country (Geo-blocking)  
- Blocking malicious IPs  
- Applying rate limiting  

---

### 🛠️ Common Tools

- API Gateway  
- WAF (Web Application Firewall)  

---

## 2️⃣ Threat Detection (Attack Detection)

### 📌 What is it?

> 👉 Analyzing traffic to identify suspicious or malicious activity

---

### 🔍 Detects:

- Attacks  
- Fraud attempts  
- Abnormal behavior  

---

### 💡 Example

> 🚨 A single user sends **1000 requests in one minute**

---

## 3️⃣ Control Validation (Security Verification)

### 📌 What is it?

> 👉 Ensuring that security controls are actually working

---

### ✔️ Verifies:

- Firewall rules  
- API Gateway policies  
- Security configurations  

---

# 🧠 Types of Monitoring

---

## 🟢 Proactive Monitoring (Preventive)

### 📌 Behavior

- Blocks malicious requests immediately  

---

### 💡 Example

> ❌ Request without token → Blocked instantly  

---

## 🟡 Reactive Monitoring (Detect & Alert)

### 📌 Behavior

- Allows request  
- Logs activity  
- Sends alerts  

---

### 📌 Used When:

- There is not enough context to block safely  

---

# 📊 Benefits of Monitoring

---

## 1️⃣ Logging (Logs)

- Record all requests  
- Essential for post-attack analysis  

---

## 2️⃣ Incident Response

- Understand how the attack happened  
- Investigate and fix vulnerabilities  

---

## 3️⃣ API Discovery

- Detect undocumented APIs  
- Identify Shadow APIs  

---

# ⚠️ Biggest Challenge in API Monitoring

> ❗ API attacks often look like normal traffic

---

## 📌 Example: Easy vs Hard Detection

### ❌ SQL Injection (Easy to Detect)


GET /users?id=1 OR 1=1


✔️ Clearly malicious  

---

### ❗ BOLA Attack (Hard to Detect)


DELETE /transfer/123
Authorization: valid-token


✔️ Valid user  
✔️ Valid token  
✔️ Valid endpoint  

> 💥 But the user does NOT own the resource 😈

---

## 🧨 Why is This Hard?

Because security tools:

- ❌ Do NOT understand data ownership  
- ❌ Do NOT understand business logic  

---

## 📌 Real Scenario


POST /sell-bitcoin?id=123


> ❗ The system does not know if the user owns that bitcoin

---

# 💡 Critical Insight

> 🔥 Monitoring alone is NOT enough

---

Even organizations using:

- WAF  
- SIEM  
- Bot protection  

Can still be breached because:

> ❗ API attacks look like legitimate traffic

---

# 🛠️ Monitoring Tools

- API Gateway  
- Web Application Firewall (WAF)  
- SIEM systems  
- Log management platforms  
- Runtime API security tools  

---

# 🧠 Relationship with Other Pillars

| Pillar      | When Used        |
|------------|-----------------|
| Governance | Before development |
| Testing    | Before deployment |
| Monitoring | After deployment  |

---

# 🧪 Why Testing is Still Needed

> ❗ Monitoring detects attacks  
> ❗ Testing prevents them before they happen  

---

# 🔑 Final Takeaway

> 🧾 Monitoring detects attacks…  
> ❗ But it cannot always stop them

---
