# 🛡️ API2:2023 - Broken Authentication

In this module, I learned about **Broken Authentication**, a critical flaw where APIs lack proper mechanisms to verify a user's identity or protect the authentication process from abuse.

---

## 🔑 What is Broken Authentication?
It happens when an API has weak, incorrectly implemented, or **completely missing** authentication. This allows attackers to:
* **Brute Force:** Guess passwords or tokens.
* **Credential Stuffing:** Use leaked passwords from other sites.
* **Anonymous Access:** Query sensitive data without logging in at all.

---

## 💡 Real-World Case Study: Duolingo
* **The Vulnerability:** An unsecured API endpoint allowed anyone to check if an email belonged to a registered user.
* **The Attack:** By simply appending an email to the URL (e.g., `api.duolingo.com/users?email=test@example.com`), the API returned the user's profile, learning progress, and streak.
* **The Scale:** Over **2 million records** were exposed. 
* **The Lesson:** Even if the data seems "non-sensitive" (like a learning streak), it can be used for targeted phishing or doxing.

---

## 🏗️ Common Weaknesses in APIs
1.  **Missing Authentication:** APIs left "wide open" because developers assume they are hidden.
2.  **Weak Tokens:** Using simple or non-expiring API keys.
3.  **Lack of Rate Limiting:** Allowing an attacker to try millions of passwords without being blocked (No CAPTCHA or 2FA).
4.  **Sensitive Info in URLs:** Passing API keys or session IDs directly in the URL instead of the Header.



---

## 🛠️ Red Team Insights
As a Red Teamer, I look for **Broken Authentication** by:
* Checking if I can access `/api/v1/admin/users` without a token.
* Testing if the API blocks me after 100 failed login attempts.
* Inspecting Android APKs to find **Hardcoded API Keys** that should have been kept secret.

---

## ✅ Best Practices for Prevention
* **Multi-Factor Authentication (2FA):** Always require more than just a password for sensitive actions.
* **Rate Limiting:** Block IPs or users that perform too many requests in a short time.
* **Standard Protocols:** Use secure standards like **OAuth2** or **OpenID Connect**.
* **Don't Assume Obscurity:** "Hidden" APIs are easily found by inspecting network traffic or decompiling mobile apps.

---
**💡 Personal Reflection:** As a student of **Android Security**, I've seen many apps store API keys in plain text inside `strings.xml`. This module reinforces why this is a major "Broken Authentication" risk. My goal is to use tools like `JADX` to find these keys in real-world apps.
