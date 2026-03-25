# 🧠 API Security - Attack Vectors & Testing Strategy

## 🔴 What Are Attack Vectors?

Attack vectors are:

> 👉 The methods attackers use to access or exploit a system

---

# 🧨 Top 4 API Attack Vectors

---

## 1️⃣ 🔐 Authentication & Authorization Attacks

### 📌 Concept

Exploiting weaknesses in:

- Authentication (login)  
- Authorization (permissions)  

---

### 💡 Examples

- Weak or predictable tokens  
- Insecure sessions  
- Missing authorization checks  

---

### 🎯 Goal

- ❌ Access without permission  
- ❌ Perform unauthorized actions  

---

## 2️⃣ 📦 Excessive Data Exposure

### 📌 Concept

API returns **more data than necessary**

---

### 💡 Example

Returns:
- Email  
- Password hash  
- System info  

Instead of:
- Name only  

---

### ❗ Core Problem

> ❌ Relying on the frontend to hide sensitive data  

---

## 3️⃣ ⚠️ Mass Assignment

### 📌 Concept

API accepts **all user input without filtering**

---

### 💡 Example

```json
{
  "username": "user",
  "role": "admin"
}
``` id="massassign"

> 💥 Privilege escalation

---

### ❗ Impact

- Changing user roles  
- Modifying sensitive fields  

---

## 4️⃣ 🚀 Lack of Rate Limiting

### 📌 Concept

No restriction on request volume

---

### 💣 Attacks

- Brute force  
- Spam requests  
- DDoS  

---

### 💥 Impact

- Server overload  
- Account compromise  

---

# 🧪 API Testing Types

---

## 1️⃣ SAST (Static Testing)

### 📌 What is it?

- Code analysis  
- Before execution  

---

### 🛠️ Example Tools

- SonarQube  

---

## 2️⃣ DAST (Dynamic Testing)

### 📌 What is it?

- Testing during runtime  
- Simulates real attacks  

---

### 🛠️ Example Tools

- API scanners  

---

## 3️⃣ HAST (Human Testing)

### 📌 What is it?

- Manual, logic-based testing  
- Requires human thinking  

---

### 🛠️ Example Tools

- Postman (Collection Runner)  
- Burp Suite  

---

# ⚖️ Shift Left vs Shift Right

---

## 🟢 Shift Left (Best Practice)

### 📌 Meaning

> 👉 Apply security early in development

---

### 🎯 Benefits

- Early vulnerability detection  
- Lower cost 💰  
- Stronger security 🔐  

---

## 🔵 Shift Right

### 📌 Meaning

> 👉 Apply security after deployment

---

### 📌 Examples

- Monitoring  
- Firewalls  
- Detection systems  

---

# 🎯 Key Strategy

> 🔥 The best approach = Combine both

---

### ✔️ Shift Left

- Prevent vulnerabilities  

---

### ✔️ Shift Right

- Detect and respond to attacks  

---

# 🔥 Smart Summary

---

## 🧠 Attackers Focus On:

- Authorization  
- Data exposure  
- Input manipulation  
- System overload  

---

## 🛡️ You Defend Using:

- Input validation  
- Strong authorization  
- Rate limiting  
- Security testing:
  - SAST  
  - DAST  
  - Manual testing  

---

# 🔑 Final Takeaway

> 🔐 API Security = Understanding how attackers think…  
> And building defenses at every stage

---
