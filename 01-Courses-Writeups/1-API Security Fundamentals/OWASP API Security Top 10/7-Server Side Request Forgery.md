# OWASP API Security Top 10 - API7: Server-Side Request Forgery (SSRF)

## 🧠 Overview
Server-Side Request Forgery (SSRF) is a critical vulnerability that allows an attacker to:

> ❗ Make the server send requests on their behalf

Instead of attacking directly, the attacker tricks the server into performing the attack.

> 😈 The server becomes the attack tool

---

## 🎯 Core Concept

Imagine an API that accepts a URL from the user:


https://example.com/fetch?url=


A normal user would input:


https://linkedin.com/user


---

But an attacker submits:


http://localhost/etc/passwd


---

## 💥 What Happens?

- The server processes the request
- Fetches the data
- Returns sensitive information

> ❗ The server unknowingly exposes internal data

---

## 😈 Why is SSRF Dangerous?

Because the server has powerful privileges:

- Access to internal systems ❗  
- Ability to bypass firewalls ❗  
- Access to sensitive files ❗  

---

## 🔥 What Can an Attacker Do?

### 1️⃣ Access Internal Services


http://127.0.0.1/admin


> 👉 Not accessible externally, but the server can access it

---

### 2️⃣ Read Local Files


file:///etc/passwd


---

### 3️⃣ Access Cloud Metadata (Critical)


http://169.254.169.254/


> 💀 Can expose cloud credentials (e.g., AWS keys)

---

## 📌 Real-World Case: Capital One Breach

One of the most famous SSRF attacks targeted Capital One.

### What Happened?

- A misconfigured WAF (Web Application Firewall)
- Attacker exploited SSRF
- Used server privileges to access AWS S3
- Extracted sensitive data

---

### 💥 Impact

- Over **100 million records leaked**
- Highly sensitive data exposed
- Massive financial and reputational damage

---

## ⚠️ Root Cause

The issue was not only SSRF:

> ❗ Excessive permissions (overprivileged server)

---

## 🧩 How SSRF Happens

Typical vulnerable flow:

1. API accepts a URL from user input  
2. No validation is performed  
3. Server sends request to that URL  
4. Response is returned to the attacker  

> 💥 Vulnerability exploited

---

## 🛡️ Mitigation Strategies

### ✔️ 1. Never Trust User Input
- Do NOT accept arbitrary URLs without validation

---

### ✔️ 2. Use Whitelisting
Allow only trusted domains:

- `linkedin.com`
- `github.com`

Block:

- `localhost`
- `127.0.0.1`
- `169.254.169.254`

---

### ✔️ 3. Block Internal Network Access
- Prevent server access to:
  - Localhost
  - Internal services

---

### ✔️ 4. Apply Least Privilege (Very Important)
- Limit server permissions
- Only allow what is necessary

---

### ✔️ 5. Filter Protocols
Block dangerous protocols:

- `file://`
- `ftp://`
- `gopher://`

---

### ✔️ 6. Test for SSRF

Try inputs like:

- `localhost`
- Internal IPs
- DNS rebinding payloads

---

## 🔑 SSRF vs Other Vulnerabilities

| Vulnerability | Concept |
|--------------|--------|
| SQL Injection | Database manipulation |
| XSS | Execute code in browser |
| SSRF | Control server requests |

---

## 🎯 Why SSRF is Dangerous

> ❗ It turns the server into a weapon

---

## 🚀 Where to Look for SSRF

Focus on features that accept URLs:

- APIs that fetch external content  
- File upload processors  
- Webhooks  
- Image fetchers  

> 👉 These are the most common SSRF entry points

---

## 🧠 Professional Mindset

Always ask:

> 😈 "Can I make the server request something it shouldn't?"

---

## 🔥 Summary

- ✔️ Vulnerability: SSRF  
- ✔️ Attack: Force server to send requests  
- ✔️ Goal: Access internal systems or sensitive data  

---

## 🎯 Final Takeaway

> 🔥 SSRF = "Make the server attack instead of you"

---
