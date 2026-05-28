# API Pentesting Module – Reverse Engineering & Data Exposure

This module explains three extremely important skills in API penetration testing.

---

# 1. Reverse Engineering API Documentation

## Rebuilding and Understanding an API Without Official Documentation

In this section, you will learn how to:

* Discover API endpoints
* Understand how the API works
* Identify parameters
* Extract HTTP methods such as:

  * `GET`
  * `POST`
  * `PUT`
  * `DELETE`
* Understand authentication mechanisms
* Manually build Swagger/OpenAPI documentation

---

# 2. Making API Requests & Response Analysis

## Sending API Requests and Analyzing Responses

You will learn how to:

* Use Postman, Burp Suite, and cURL
* Modify API requests
* Read and analyze responses
* Understand JSON structures
* Analyze HTTP headers
* Extract tokens and sensitive data
* Understand API behavior and logic

---

# 3. Excessive Data Exposure Testing

## Testing for Sensitive Data Exposure

This is one of the most common API vulnerabilities.

### Expected Response

```json
{
  "username": "ahmed"
}
```

### Vulnerable Response

```json
{
  "username": "ahmed",
  "email": "test@test.com",
  "password_hash": "...",
  "isAdmin": true
}
```

This is considered:

# Excessive Data Exposure

---

# The Real Goal of This Module

Learn how to:

* Understand undocumented APIs
* Build a complete API map
* Analyze requests and responses
* Detect sensitive data leakage
* Start real-world API security analysis

---

# Final Outcome

After completing this module, you will be able to:

* Reverse engineer APIs
* Analyze requests and responses
* Discover hidden endpoints
* Detect data leakage
* Build Postman collections
* Understand applications without source code
