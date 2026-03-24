# API Security Fundamentals - Attack Patterns & Threat Modeling

## 🧠 Overview
After learning the OWASP API Top 10 vulnerabilities, the next step is to understand:

> ❓ Why do attacks happen?  
> ❓ And how can we actually prevent them?

---

## 🧩 Main Causes of API Breaches

### ⚠️ Top 4 Attack Patterns

---

### 1️⃣ Rate Limiting Abuse (High-Volume Attacks)

- Attackers send massive numbers of requests  
- Used for:
  - Data harvesting  
  - Brute force attacks  

---

### 📌 Example

> Extracting large datasets by sending millions of requests

---

### ❗ Important Note

Rate limiting alone is NOT enough.

---

### 2️⃣ Broken Authorization (Most Critical)

- User A can access User B’s data  

> 🔥 This is the cause of most real-world breaches

---

### 3️⃣ Broken Authentication

- APIs without proper login  
- Weak or predictable tokens  

---

### 4️⃣ Excessive Data Exposure

- APIs return more data than necessary  

---

## 💡 Critical Insight

> 👉 90% of attacks = Authorization + Authentication + Data Exposure

---

## 🧠 Is Rate Limiting Enough?

> ❌ No

---

### Why?

Attackers can:

- Slow down requests (stay under limits)  
- Use thousands of IP addresses  
- Use proxies and distributed attacks  

---

> 👉 Rate limiting is a **defense layer**, not a complete solution

---

## 🧭 Threat Modeling

### 🪜 Step-by-Step Process

---

### 1️⃣ Identify Attack Surface

- List all APIs  
- Understand how they are used  
- Identify who can access them  

---

### 2️⃣ Discover Vulnerabilities

Look for:

- Authorization issues  
- Business logic flaws  
- External API risks  

---

### 3️⃣ Evaluate Risks

#### 📊 Likelihood
- How easy is it to exploit?

#### 💥 Impact
- What happens if exploited?

---

### 4️⃣ Calculate Risk


Risk = Threat × Vulnerability × Likelihood × Impact


---

## 🎯 The Most Important Question in Security

> 🤔 What does the attacker want?

---

### 🔓 Common Targets

- Personal data (PII)  
- Credit card information  
- Company data  
- Free services (fraud)  
- Sensitive systems (banking, energy)  

---

## 🔗 Where Do APIs Fit In?

> 👉 APIs are the backbone of modern systems

---

### Examples:

- Mobile apps rely on APIs  
- Websites rely on APIs  
- Microservices = APIs  

---

> 💥 If APIs are vulnerable → the entire system is at risk

---

## ⚠️ Example Risks

### 🧟 Unknown APIs (Zombie APIs)

- APIs that exist without team awareness  
- Often outdated and vulnerable  

---

### 📌 Real Impact

- Example: Optus breach → millions of users exposed  

---

## 🧠 Attacker Mindset

Always ask:

- Can I access sensitive data?  
- Are there hidden APIs?  
- Can I bypass authentication?  
- Can I send excessive requests?  

---

## 🛡️ Final Goal

> 👉 Prioritize risks based on severity

---

### Risk Levels

- 🔴 High Risk → Fix immediately  
- 🟡 Medium Risk → Fix later  
- 🟢 Low Risk → Monitor  

---

## 🧠 Final Takeaways

- ✔️ Most attacks come from:
  - Authorization  
  - Authentication  
  - Data Exposure  

- ✔️ Rate limiting is useful, but not sufficient  

- ✔️ Always ask:
  > ❓ What do I have?  
  > ❓ What does the attacker want?  

---

## 🔑 Golden Rule

> 🔐 Real security starts with **Threat Modeling**

---
