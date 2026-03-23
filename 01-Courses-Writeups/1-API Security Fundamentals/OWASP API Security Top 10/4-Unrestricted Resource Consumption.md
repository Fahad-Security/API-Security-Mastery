# OWASP API Security Top 10 - API4: Unrestricted Resource Consumption

## 🧠 Overview
API4: Unrestricted Resource Consumption is one of the most dangerous vulnerabilities in modern APIs. It occurs when an API fails to enforce proper limits on how clients can consume its resources.

In simple terms, the API allows users (or attackers) to send an unlimited number of requests, consume excessive data, or use system resources without restriction.

> ❗ This means an attacker can abuse the API without being stopped.

---

## 📌 What Does This Mean in Practice?

When an API does not enforce limits, an attacker can:

- Send thousands or even millions of requests
- Continuously and without interruption
- Operate without being blocked or detected

This leads to resource exhaustion and potential system failure.

---

## 🔥 Common Vulnerability Scenarios

### 1️⃣ No Rate Limiting
The API does not restrict how many requests a user can send.

- Attackers can send **hundreds or thousands of requests per second**
- No `429 Too Many Requests` response is triggered

---

### 2️⃣ No Data Size Limits
The API returns large amounts of data without restriction.

- Attackers can request huge datasets repeatedly
- Leads to bandwidth and memory exhaustion

---

### 3️⃣ No Timeout Mechanism
Requests are allowed to run indefinitely.

- Long-running requests consume server resources
- Can lead to thread or connection exhaustion

---

### 4️⃣ Unrestricted File Uploads
The API allows uploading files without size limits.

- Attackers can upload extremely large files
- Storage and processing resources get exhausted

---

## ⚠️ Impact

If exploited, this vulnerability can lead to:

- 💥 Denial of Service (DoS)
- 🐌 Severe application slowdown
- 📉 Server resource exhaustion (CPU, RAM, bandwidth)
- 📊 Mass data harvesting

---

## 🚨 Real-World Example: Trello API Abuse

A real-world example of this vulnerability was discovered in the Trello API.

### The Vulnerable Endpoint
/api/user?email=test@gmail.com

### What Did It Return?

- Whether the email exists
- Information about the user

---

### Attack Execution

The attacker:

1. Collected **500 million email addresses**
2. Sent **500 million API requests**
3. Extracted user-related data

---

### How Was Protection Bypassed?

The attacker avoided detection by:

- Not sending requests at a high speed
- Distributing requests across multiple IP addresses
- Operating slowly and stealthily

> 🧠 The attack was not noisy — it was smart.

---

## 🧠 Key Lesson

> Attacks are not always fast.  
> Some of the most dangerous attacks are slow, distributed, and stealthy.

---

## 🔥 Critical Insight

Even if protections exist, such as:

- Firewalls
- Basic rate limiting

> ❗ Skilled attackers can still bypass them.

---

## 💡 Mitigation Strategy (Atlassian Fix)

To fix the issue, Atlassian introduced:

✔️ Authentication requirements for API access

---

## 🧠 Why Authentication Matters

### Before:
- Anonymous requests
- No accountability
- Impossible to track attackers

### After:
- Requests linked to authenticated users
- Easier detection and blocking

---

## 🔥 Comparison

| Scenario        | Result                     |
|----------------|--------------------------|
| Without Login  | Cannot identify attacker |
| With Login     | Can track and block user |

---

## 🧠 Attacker Mindset

A beginner thinks:

> "Is this API vulnerable?"

A professional attacker thinks:

> 😈 "What happens if I push this API to its limits?"

---

## 🛠️ How to Test This Vulnerability

### Step 1: Send Multiple Requests

Use tools such as:

- Burp Suite Intruder
- Custom scripts (Python, Bash, etc.)

---

### Step 2: Monitor Responses

Check for:

- Rate limiting responses (`429`)
- Temporary or permanent bans
- Performance degradation

---

### Step 3: Try Different Techniques

- Use multiple IP addresses
- Send requests without authentication
- Increase payload size
- Test different endpoints

---

## 🔥 Practical Example
GET /api/search?q=test

### Test Strategy

- Send 100 requests
- Then 1000 requests

---

### 🚨 Red Flag

If you do **NOT** receive:
429 Too Many Requests

> 💥 There is a high likelihood of vulnerability

---

## 🧠 Professional Thinking

Instead of asking:

> "Is there a vulnerability?"

Ask:

> 😈 "How much load can this system handle before breaking?"

---

## 🚀 Hands-On Practice

To fully understand this vulnerability:

1. Choose a legal target (lab or authorized scope)
2. Send multiple requests
3. Observe:
   - Does the API block you?
   - Does performance degrade?
   - Are there any protections?

---

## 🔥 Summary

- ✔️ Vulnerability: Lack of resource and usage limits  
- ✔️ Attack Method: High-volume or strategic requests  
- ✔️ Goal: Resource exhaustion or large-scale data extraction  
- ✔️ Defense: Rate limiting, authentication, quotas, and monitoring  

---
