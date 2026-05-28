# Lesson Summary: Reverse Engineering APIs

In this module, we learned how to **reverse engineer APIs** when no official documentation, Swagger, or OpenAPI specifications are available.

The main objective is to build a complete request collection, understand how the API works, analyze responses, and identify vulnerabilities such as **Excessive Data Exposure**.

---

# Core Idea

When an API is undocumented, you must:

* Monitor traffic
* Collect requests
* Organize endpoints
* Understand methods and parameters
* Build your own API collection

---

# Methods Used

## 1. Using Postman Manually

This approach works by:

* Running a proxy inside Postman
* Routing browser traffic through the proxy
* Using the application normally
* Capturing all requests

---

## Steps

1. Create a new Workspace
2. Create a new Collection
3. Enable **Capture Requests**
4. Start the proxy on port:

```bash
5555
```

5. Configure the browser proxy to:

```bash
127.0.0.1:5555
```

6. Use the application normally:

* Login
* Edit account
* Upload files
* Change email
* Add vehicle
* Refresh GPS location
* Etc.

---

# What Happens Next?

Postman will start collecting:

* Endpoints
* Headers
* JSON bodies
* HTTP methods
* Tokens
* Responses

Then you can filter important API requests such as:

```bash
/api/
/api/v2/
/auth/login
/graphql
```

---

# Organizing the API Collection

After collecting requests, organize them into folders such as:

```bash
identity/
community/
workshop/
```

This makes API analysis much easier.

---

# Why Postman Is Useful Here

Postman helps you:

* Understand API behavior
* Replay requests
* Modify headers
* Edit JSON bodies
* Test vulnerabilities later

---

# 2. Using MITMProxy + Swagger

This method is more powerful because it can automatically generate Swagger/OpenAPI specifications.

---

# Workflow

## Step 1: Start MITMProxy

Run:

```bash
mitmweb
```

The web interface will be available on:

```bash
8081
```

The proxy listener will run on:

```bash
8080
```

---

## Step 2: Route Traffic Through the Proxy

Then use the application normally:

* Login
* Password reset
* Upload files
* Register vehicle
* GPS refresh
* Etc.

---

## Step 3: Save Traffic

MITMProxy will save a file called:

```bash
flows
```

---

## Step 4: Convert Traffic to Swagger

Using:

```bash
mitmproxy2swagger
```

Example:

```bash
sudo mitmproxy2swagger -i flows -o spec.yaml -p https://target.com -f flow
```

---

# Output

The tool generates:

```bash
spec.yaml
```

This is a complete OpenAPI/Swagger specification containing:

* API endpoints
* HTTP methods
* Parameters
* Response codes
* JSON examples
* Request bodies

---

# Cleaning the Swagger File

The tool automatically adds:

```yaml
ignore:
```

for some endpoints.

You should remove `ignore` from important paths such as:

```yaml
/api/v2/
/api/auth/
/identity/
/workshop/
```

---

# Re-running the Tool

After editing the file, run:

```bash
mitmproxy2swagger ...
```

with:

```bash
--examples
```

to include request and response examples.

---

# Viewing Swagger

The generated specification can be opened inside:

* Swagger Editor
* Postman
* Burp Suite
* Insomnia

---

# Benefits of the Generated Swagger

You can identify:

## HTTP Methods

```http
GET
POST
PUT
DELETE
PATCH
```

## Parameters

```json
id
email
token
```

## Data Types

```json
application/json
```

## Response Codes

```http
200
401
403
500
```

---

# Vulnerability Discovery

The instructor focused on:

## Excessive Data Exposure

This happens when the API returns more data than necessary.

Example:

```json
{
  "username":"test",
  "email":"a@a.com",
  "passwordHash":"...",
  "internalRole":"admin"
}
```

This represents a serious security issue.

---

# Final Result

After completing the process, you will have:

* A complete API collection
* A Swagger/OpenAPI specification
* A full understanding of the attack surface
* All important endpoints
* The ability to test vulnerabilities efficiently

---

# Simplified Workflow

```text
Target App
   ↓
Proxy Traffic
   ↓
Capture Requests
   ↓
Filter API Calls
   ↓
Build Collection
   ↓
Generate Swagger
   ↓
Analyze Endpoints
   ↓
Find Vulnerabilities
```

---

# Tools Used

| Tool       | Purpose                          |
| ---------- | -------------------------------- |
| Postman    | Collect and organize requests    |
| mitmproxy  | Intercept traffic                |
| Swagger    | Document and analyze APIs        |
| Postman    | Replay and test requests         |
| Burp Suite | Analyze and test vulnerabilities |
