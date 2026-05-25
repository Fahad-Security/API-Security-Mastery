# What Is an API?

An API is the interface that allows an application to communicate with the server.

Example:

When you press "Login" in an Android application, the app does not verify the password itself.  
Instead, it sends a request to an API such as:

```http
POST /api/v1/login
```

And the server responds with:

```json
{
  "token": "abc123"
}
```

So:

- The application = the interface
- The API = the real brain
- The server = the database and business logic

This is why most modern vulnerabilities exist inside APIs.

---

# Core Idea of the Lesson

Before attacking an API, you must:

1. Discover its existence
2. Identify endpoints
3. Understand how it works
4. Determine whether it is Public or Private
5. Start security testing

---

# Types of APIs

## 1. Public APIs

These APIs are designed for the public or developers.

Examples:

- Weather APIs
- Payment APIs
- Mobile application APIs

Usually, they have clear documentation.

Examples:

```text
https://api.target.com/v1/
```

Or:

```text
https://target.com/developers
```

---

## 2. Partner APIs

These APIs are intended only for partner companies.

Examples:

- Delivery company APIs
- Banking APIs
- Merchant APIs

They are slightly harder to discover.

---

## 3. Private APIs

These are the most important and dangerous in Bug Bounty.

They are used internally within the application or company.

Usually:

- No documentation
- Hidden
- Require reverse engineering

This is where real ethical hacking begins.

---

# How Do We Discover APIs in Practice?

---

# Method 1 — Using the Application Normally

This is the most important step.

Open the application and use it as a normal user.

Monitor actions such as:

- Login
- Image uploads
- Search
- Account editing
- Password reset

Every action usually triggers an API request.

---

# Practical Setup

## Required Tools

### On Android

- Burp Suite
- HTTP Toolkit
- mitmproxy

---

# Steps

## 1. Start Burp Suite

Enable the proxy.

---

## 2. Connect the Phone to the Proxy

WiFi → Proxy → Manual

Set:

- Computer IP
- Port 8080

---

## 3. Install the Burp Certificate

So HTTPS traffic can be inspected.

---

## 4. Open the Application

Now you will see requests like:

```http
POST /api/v1/auth/login
GET /api/v1/profile
GET /api/v1/orders
```

At this point, you have discovered the API.

---

# How Do You Identify an API?

The lesson mentioned several important indicators.

---

# Indicator 1 — URL Names

Examples:

```text
/api/
/v1/
/graphql
/rest
```

Real examples:

```text
https://api.target.com/v1/users
https://target.com/api/login
```

---

# Indicator 2 — JSON Responses

If you see:

```json
{
  "username": "admin"
}
```

It is most likely an API.

---

# Indicator 3 — Headers

Examples:

```http
Content-Type: application/json
```

Or:

```http
Accept: application/json
```

These are very strong indicators.

---

# Indicator 4 — Error Messages

Example:

```json
{
  "message": "Missing authorization token"
}
```

This means:

- The endpoint exists
- It only requires authorization

This is valuable information.

---

# Real Practical Workflow

Open Burp Suite and search for:

```text
/api/
/graphql
/v1/
/v2/
```

Then monitor:

- POST
- PUT
- DELETE

Because these methods are usually more dangerous than GET.

---

# Method 2 — Searching Inside the Website

Sometimes the website publicly exposes APIs.

Look for:

- Developers
- API Docs
- Swagger
- OpenAPI

---

# Common API Documentation Paths

## Swagger

You will often find:

```text
/swagger
/swagger-ui
/api-docs
/openapi.json
```

---

# Why Is Swagger Important?

Because it exposes:

- All endpoints
- Parameters
- Authentication methods
- Request bodies

Meaning:

> A complete attack map.

---

# Practical Example

If you find:

```text
https://target.com/swagger-ui
```

You may see:

```http
GET /users
POST /users
DELETE /users/{id}
```

Now you can begin testing:

- IDOR
- Authentication bypass
- Mass assignment
- Rate limiting

---

# Method 3 — Searching JavaScript Files

This is one of the strongest techniques.

---

# Practical Steps

Open the website.

Then press:

```text
Ctrl + Shift + I
```

Go to:

- Sources
- JavaScript files

Or use:

```bash
curl https://target.com/app.js
```

---

# What Are We Searching For?

Search for:

```text
/api/
/graphql
bearer
token
axios
fetch(
```

---

# Real Example

You may find:

```javascript
axios.get("/api/v1/admin/users")
```

Or:

```javascript
const API = "https://api.target.com/v2/"
```

This is how hidden APIs are discovered.

---

# Method 4 — GitHub Recon

The lesson mentioned GitHub because it is a gold mine.

Search for:

```text
target api github
```

Or:

```text
site:github.com target.com api
```

---

# What Are We Looking For?

- Postman Collections
- Swagger files
- API keys
- Endpoints

---

# Dangerous Example

You may discover:

```json
{
  "baseUrl": "https://api.target.com/v1/"
}
```

Or:

```text
API_KEY=sk_live_xxx
```

---

# Method 5 — Postman

Many developers accidentally expose Postman collections publicly.

Search for:

```text
target postman collection
```

You may find the entire API already prepared.

---

# Method 6 — Reverse Engineering Android Applications

This is one of the most important Bug Bounty skills.

---

# Practical Workflow

## Decompile the APK

Use:

```bash
apktool d app.apk
```

Or:

```bash
jadx-gui app.apk
```

---

# What Should You Search For?

Look for:

```text
https://
api
token
graphql
baseUrl
retrofit
okhttp
```

---

# Real Example

You may find:

```java
BASE_URL = "https://api.target.com/v3/"
```

Or:

```java
@GET("/api/v1/user/profile")
```

This allows you to extract complete endpoints.

---

# Method 7 — Monitoring Dynamic Traffic

If the application uses encryption or SSL Pinning:

Use:

- Frida
- Objection
- SSL Unpinning

Then inspect the real traffic.

---

# Why Is This Phase Important?

Because discovering the API attack surface is more important than exploitation itself.

If you fail to discover:

- Endpoints
- Parameters
- Hidden APIs

You will never find strong vulnerabilities.

---

# How Does a Professional Think During API Recon?

A professional does not search for just one endpoint.

Instead, they build a complete map.

| Component | Objective |
|---|---|
| Authentication | How login works |
| Roles | Is there an Admin role? |
| Versioning | v1 / v2 |
| Hidden APIs | Unused in the UI |
| Internal APIs | Company-only services |
| Mobile APIs | Different from web APIs |
| GraphQL | Sometimes more dangerous |
| Upload APIs | File upload functionality |
| Export APIs | Potential data leakage |

---

# Professional Workflow for Real Applications

## Phase 1

Run the application through Burp Suite.

---

## Phase 2

Record every endpoint.

Example:

```text
/api/v1/login
/api/v1/user
/api/v1/upload
/api/v1/admin
```

---

## Phase 3

Categorize them:

- Authentication
- Upload
- Admin
- Payments
- Search

---

## Phase 4

Begin security testing:

- IDOR
- BOLA
- Broken Authentication
- Rate limiting issues
- SSRF
- File upload vulnerabilities
- Mass assignment

---

# Most Important Point in the Lesson

The lesson states:

> If documentation does not exist, you must learn reverse engineering.

This is completely true.

In real Bug Bounty programs:

- Most important APIs are hidden
- Require application analysis
- Require traffic monitoring
- Require JavaScript analysis
- Require APK reverse engineering

---

# Real Bug Bounty Example

An Android application contains:

```text
https://internal-api.target.com/v1/
```

But this API is not publicly used.

After testing, you discover:

```http
GET /v1/admin/users
```

And it returns sensitive data because of:

- Broken Access Control
- Missing Authorization

At this point, simple recon becomes a Critical vulnerability.

---

# Professional Summary

API discovery depends on:

1. Traffic monitoring
2. Application analysis
3. JavaScript analysis
4. GitHub/Postman reconnaissance
5. Reading Swagger/OpenAPI documentation
6. Reverse engineering

The real skill is not just running tools.

It is:

- Understanding application logic
- Connecting endpoints together
- Predicting hidden APIs
- Knowing where vulnerabilities may exist
