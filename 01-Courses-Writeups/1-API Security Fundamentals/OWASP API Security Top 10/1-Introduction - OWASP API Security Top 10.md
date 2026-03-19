# 🛡️ Module : Introduction to OWASP API Security Top 10

In this module, I was introduced to the **OWASP (Open Worldwide Application Security Project)** and its specific focus on API vulnerabilities. Understanding this framework is essential for any professional Penetration Tester.

---

## 🌐 What is OWASP?
* **OWASP** is a non-profit foundation that works to improve the security of software.
* While they are famous for the "Web Top 10," they realized in 2019 that APIs have **unique threats** that require a dedicated list.
* **Current Standard:** This course covers the **2023 Edition**, which reflects the latest shifts in the API threat landscape.

---

## ⚠️ The Reality of API Breaches
The instructor highlighted that even major companies with top-tier defenses (WAFs, Code Scanning, Traditional Pentesting) are still falling victim to API attacks. 

### Why do traditional defenses fail?
Traditional tools often look for "signatures" of known attacks (like a malicious script). However, API attacks often look like **legitimate traffic** but exploit the **Business Logic**.

### Common Threat Vectors in APIs:
* **Unauthorized Trading:** Exploiting financial APIs.
* **Account Harvesting:** Stealing massive amounts of user data.
* **Data Tampering:** Changing information (e.g., prices or permissions) directly through the API.
* **Third-Party Exposure:** When a partner's insecure API leads to a breach in your system.

---

## 🛠️ The Roadmap Ahead
Instead of a generic overview, each of the 10 vulnerabilities will be explored in depth through:
1. **Definition:** Understanding the risk vector.
2. **Real-World Examples:** Analyzing actual breaches.
3. **Best Practices:** Learning how to remediate and prevent these flaws.



---

### 💡 Red Team Reflection
As I specialize in **Android and Red Teaming**, I've noticed that many mobile apps rely on the assumption that "no one will see the API calls." This module confirms that **security through obscurity is a myth.** The fact that companies with WAFs (Web Application Firewalls) are still getting breached proves that we need **Manual Logic Testing**—a skill I am currently building.

**Next Step:** Deep dive into **API1:2023 - Broken Object Level Authorization (BOLA)**.
