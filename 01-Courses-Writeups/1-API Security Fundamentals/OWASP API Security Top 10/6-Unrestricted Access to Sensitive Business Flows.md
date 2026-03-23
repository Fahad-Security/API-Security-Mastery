# OWASP API Security Top 10 - API6: Unrestricted Access to Sensitive Business Flows

## 🧠 Overview
API6 focuses on one of the most advanced and dangerous types of vulnerabilities:

> ❗ Exploiting **Business Logic** instead of a direct technical flaw

In this case, the application works exactly as intended…

> 😈 But attackers use it in an unintended (and malicious) way

---

## 🎯 What is a "Business Flow"?

A **Business Flow** represents the normal steps inside an application.

### Examples:

- User registration  
- Login process  
- Password reset  
- Purchasing a product  

> 👆 These are called application workflows (flows)

---

## ⚠️ Where is the Problem?

Developers usually ask:

> "Does the application work correctly?"

But attackers ask:

> 😈 "Can I abuse this flow in an unexpected way?"

---

## 💣 Real-World Style Example (Instagram Scenario)

### 🎯 Normal Flow (Happy Path)

1. User clicks **"Forgot Password"**
2. System sends a **6-digit code**
3. User enters the code
4. User resets password  

✔️ Everything works correctly

---

## 😈 Attacker Mindset

The attacker thinks:

> A 6-digit code = 1,000,000 possible combinations

---

## 🧨 The Attack (Brute Force Logic Abuse)

The attacker starts guessing:


000001
000002
000003
...


And sends API requests rapidly.

---

## 🚧 Existing Protections

- ⏱️ Time limit (e.g., 10 minutes)
- 🔢 Attempt limit (e.g., 200 attempts)

---

## 💥 The Real Vulnerability

The system limits attempts based on:

> ❌ IP address only

---

## 😈 How the Attacker Bypasses It

- Changes IP address
- Gets a fresh 200 attempts
- Repeats the process

---

## 🔥 Result

> 💥 The attacker can try all 1,000,000 combinations in a short time

---

## 💡 Root Cause

This is NOT a technical vulnerability like:

- SQL Injection ❌  
- XSS ❌  

Instead, it is:

> 🧠 A **Logic Flaw** in how the system was designed

---

## 🧠 Golden Insight

> ⚡ This vulnerability depends on **thinking outside the box**

---

## 🔍 How to Discover This Vulnerability

Ask yourself:

- 🤔 Is there a code that can be guessed?
- 🤔 Is there a limit that can be bypassed?
- 🤔 Can the process be repeated?
- 🤔 Does the system rely only on IP?
- 🤔 Can the attack be automated?

---

## 🛡️ Mitigation Strategies

### ✔️ 1. Do NOT Rely on IP Only
- Bind attempts to the **user account**, not IP

---

### ✔️ 2. Reduce Attempt Limits
- Example: 200 → 5 attempts only

---

### ✔️ 3. Invalidate Codes Quickly
- After a few failed attempts → expire the code

---

### ✔️ 4. Use Strong Random Codes
- Avoid predictable or incremental patterns

---

### ✔️ 5. Add Delays (Rate Control)
- Slow down repeated attempts

---

## 🔥 Why This Vulnerability is Dangerous

- ❗ Not detected by automated scanners  
- ❗ Requires deep understanding of the application  
- ❗ Depends on creativity and logic analysis  

---

## 🧠 Professional Mindset

A beginner looks for:

> "Technical vulnerabilities"

A professional looks for:

> 😈 "Ways to break the logic of the system"

---

## 🎯 Important Comparison

| Vulnerability Type | Concept |
|------------------|--------|
| BOLA | Accessing unauthorized data |
| Broken Authentication | Weak login mechanisms |
| BOPLA | Modifying object properties |
| Resource Consumption | Overloading the system |
| Function Level Auth | Unauthorized actions |
| 🧠 Business Logic | Abusing how the system works |

---

## 🚀 Hands-On Practice

To master this vulnerability:

1. Choose a real or lab application  
2. Analyze its workflows (flows)  
3. Try to:
   - Repeat steps
   - Skip steps
   - Automate actions  
4. Think:
   > 😈 "What if I use this flow in a way the developer never expected?"

---

## 🔥 Summary

- ✔️ Vulnerability: Business Logic Flaw  
- ✔️ Attack: Abuse normal application flows  
- ✔️ Goal: Bypass protections and gain advantage  

---
