# 🛡️ API1:2023 - Broken Object Level Authorization (BOLA)

In this module, I studied **BOLA**, the most frequent and dangerous vulnerability in the OWASP API Security Top 10. Understanding BOLA is a game-changer for my **Red Team** and **Android Security** research.

---

## 🔍 What is BOLA?
**Broken Object Level Authorization (BOLA)** occurs when an application does not properly verify if the user making a request has permission to access a specific object (data).

* **The Core Question:** Can User A access User B’s data?
* **The Flaw:** The server checks **WHO** you are (Authentication) but fails to check **WHAT** you are allowed to see (Authorization).

---

## 💡 Real-World Case Studies

### 1. Coinbase (The $43,000 Logic Flaw)
* **The Attack:** A researcher manipulated a valid trade request. By changing the `product_id` from Ethereum (which he owned) to Bitcoin (which he did not own), he bypassed the logic.
* **The Result:** He sold $1,000 of Ethereum but the system processed it as a sale of Bitcoin, potentially worth much more.
* **Lesson:** The API validated price and quantity but **missed the logic check** for asset ownership.

### 2. Peloton (Authentication vs. Authorization)
* **The Attack:** An API allowed anyone to query the 4-million-user database.
* **The "Fix" Failure:** Peloton first added a login requirement. However, *any* logged-in user could still query *any* other user's private data.
* **Lesson:** Requiring a password (Authentication) is not enough. You must also check if the logged-in user is authorized to see that specific record.

---

## 🛠️ Red Team Insights: Why BOLA is Unique?
1.  **Invisible to WAFs:** BOLA requests look like perfectly legal traffic. There is no "malicious code" (like `<script>` or `OR 1=1`), just a change in an ID.
2.  **UI is a Mask:** User Interfaces (Web or Android) often restrict what you can click. But by hitting the API directly (via **Postman** or **Burp Suite**), we bypass all UI-based security.
3.  **Predictable IDs:** If an API uses IDs like `/api/users/1001`, a Red Teamer will immediately try `/api/users/1002`.

---

## ✅ Best Practices for Prevention
* **Authorization Checks:** Implement fine-grained access control at the code level for every single request.
* **Use UUIDs:** Instead of predictable IDs (1, 2, 3), use random strings (e.g., `550e8400-e29b-41d4-a716...`).
* **Shift Left:** Security teams must be involved during the design phase, not just after the code is written.

---
**💡 Android Security Tip:** In Mobile Pentesting, I will look for BOLA by decompiling APKs to find API endpoints and then fuzzing the IDs in the request headers to see if I can access other users' profiles.
