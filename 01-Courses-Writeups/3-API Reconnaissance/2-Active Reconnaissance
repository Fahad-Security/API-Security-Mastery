# Active Reconnaissance for API Penetration Testing

This lesson explains one of the most important phases in API penetration testing:

# Active Reconnaissance

This phase is considered one of the most critical and dangerous parts of penetration testing because this is where you start interacting directly with the target and discovering:

- Hidden APIs
- Secret routes
- Admin panels
- Tokens
- Auth headers
- Versions
- Debug endpoints
- Test environments
- Swagger documentation
- Weak services

---

# Core Idea of the Lesson

Before attacking any API, you must build an:

# API Attack Surface

Meaning:

> A complete map of everything related to the API.

Such as:

- Domains
- Subdomains
- Open ports
- Protocols
- Endpoints
- Parameters
- Headers
- Authentication methods
- Versions
- Hidden APIs

---

# Difference Between Passive and Active Recon

## Passive Recon

Without directly touching the target.

Examples:

- Google
- GitHub
- Wayback Machine
- Shodan
- crt.sh

Low risk.

---

## Active Recon

You directly interact with the server.

Examples:

- Nmap
- Gobuster
- Kiterunner
- Burp Suite
- Browser DevTools

This activity may appear in logs.

---

# The Real Goal of This Phase

Not just finding the API.

But:

# Understanding How the Application Thinks

How does it work?  
How does it communicate?  
How does authentication work?  
How is data sent?  
How is information retrieved?

---

# Professional Recon Workflow

Here is a real workflow used by professional penetration testers.

---

# Phase 1 — Launch the Target and Understand It

In this lesson, they used:

- CrAPI

A vulnerable training application.

After launching it:
they opened it in the browser and verified it was running.

---

# Phase 2 — Nmap

## Why Use Nmap?

To discover:

- Open ports
- Services
- Server types
- Technologies
- Software versions
- Additional services

---

# Important Commands

## Quick Scan

```bash
nmap 127.0.0.1
```

---

## Service and Version Detection

```bash
nmap -sV 127.0.0.1
```

### What Does It Reveal?

It can identify:

- Apache
- nginx
- OpenResty
- NodeJS
- Express
- Gunicorn

---

## Run NSE Scripts

```bash
nmap -sC -sV 127.0.0.1
```

This reveals:

- HTTP information
- SSL details
- robots.txt
- Headers
- Authentication info

---

## Scan All Ports

```bash
nmap -p- 127.0.0.1
```

This is extremely important.

Because many APIs run on:

- 8080
- 3000
- 5000
- 8000
- 8888

---

# The Mindset Here

A beginner:

> Only checks port 80.

A professional:

> Any port may contain an API.

---

# Why Did They Find MailHog?

Because they performed an All Ports Scan.

They discovered:

```text
8025
```

Which was MailHog.

---

# Why Is This Valuable?

Extremely valuable.

You may obtain:

- Password reset links
- OTP codes
- Verification emails
- Session tokens
- Invite tokens

---

# How Can This Be Exploited?

In Bug Bounty programs:

If a mail server is exposed:

It may lead to:

- Account takeover
- Privilege escalation
- Password reset abuse

---

# Phase 3 — Manually Visiting Services

After discovering a port:

Open it manually in the browser:

```text
http://IP:8025
```

---

# The Key Idea

Anything you discover:
open it manually.

Do not rely only on tools.

---

# Phase 4 — Amass

## What Does Amass Do?

It gathers:

- Subdomains
- APIs
- Assets
- Certificates
- External infrastructure

---

# Why Is Amass Powerful?

Because it collects data from dozens of sources:

- Google
- GitHub
- Shodan
- crt.sh
- Wayback Machine
- AlienVault

---

# Basic Command

```bash
amass enum -passive -d target.com
```

---

# Active Enumeration

```bash
amass enum -active -d target.com
```

---

# What Are We Looking For?

Things like:

```text
api.target.com
dev-api.target.com
uat-api.target.com
test-api.target.com
internal-api.target.com
```

---

# Golden Keywords

If you see:

- dev
- test
- uat
- staging
- beta
- internal
- sandbox

These are gold mines.

---

# Why?

Because they often have:

- Weaker protection
- Debug mode enabled
- Weak authentication
- Real production data

---

# Professional Filtering

Filter results for APIs:

```bash
amass enum -passive -d target.com | grep api
```

---

# Phase 5 — Gobuster

## Purpose

Directory brute forcing.

It attempts many paths.

---

# Example

```bash
gobuster dir -u http://target.com -w wordlist.txt
```

---

# What Can It Discover?

```text
/api
/admin
/docs
/swagger
/graphql
/v1
/v2
/internal
/debug
```

---

# Important Problem Explained in the Lesson

Some servers return:

```text
200 OK
```

For everything.

Even invalid paths.

---

# Why Is This a Problem?

Because Gobuster assumes every path exists.

---

# The Solution

Filter status codes:

```bash
--exclude-status 200
```

Or:

```bash
-b 404
```

---

# Best Wordlists for APIs

Instead of generic wordlists:

Use:

- api.txt
- common-api-endpoints.txt
- graphql.txt

---

# Best Wordlist Sources

## SecLists

https://github.com/danielmiessler/SecLists

## Assetnote

https://github.com/assetnote/wordlists

---

# Phase 6 — Kiterunner

One of the most important API recon tools.

---

# Why Is It Better Than Gobuster?

Because APIs are not like traditional websites.

---

# Gobuster Thinks Like This

```text
/api
/api/admin
/api/users
```

If `/api` returns 404:
it stops.

---

# Kiterunner Thinks Like This

Even if `/api` returns 404:

It still tries:

```text
/api/v1/users
/api/v2/login
/api/internal/admin
```

Because it understands REST API structures.

---

# Important Commands

## Scan an API

```bash
kr scan http://target.com
```

---

## Use a Strong Wordlist

```bash
kr scan http://target.com -w routes-large.kite
```

---

# Best Kiterunner Wordlists

https://wordlists.assetnote.io

---

# Why Is Kiterunner So Powerful?

Because it discovers:

- Hidden APIs
- Nested APIs
- REST structures
- Versioned APIs

---

# Phase 7 — DevTools

This stage is extremely powerful.

---

# Why?

Because you can see:

- Real requests
- Headers
- Tokens
- Cookies
- JSON responses
- Endpoints

---

# Most Important Area

## Network Tab

Press:

```text
F12
```

Then:

- Network
- Reload the page

---

# What Should You Look For?

## Important Keywords

```text
/api/
/graphql
/v1/
/v2/
```

---

# What Did They Discover?

```text
/api/v2/community
/api/shop/products
```

---

# Why Is This Valuable?

Because the application did not expose these APIs to the user.

But DevTools revealed them.

---

# Most Important Thing in the Lesson

## Authorization Bearer Token

They found it inside:

```http
Authorization: Bearer eyJ...
```

---

# Why Is This Extremely Important?

This token:

- Identifies the user
- May provide full access
- Can be tested for vulnerabilities
- May contain JWT weaknesses

---

# What Should You Test After Finding It?

Try:

- IDOR
- Privilege escalation
- Role manipulation
- Token reuse
- Expired token bypass

---

# Phase 8 — Copy as cURL

This is a very professional skill.

---

# Why?

So you can transfer requests from the browser into:

- Postman
- Burp Suite
- curl
- Custom scripts

---

# Method

Right click the request:

```text
Copy -> Copy as cURL
```

---

# Then in Postman

```text
Import -> Raw text
```

---

# Benefit

You instantly get:

- Headers
- Cookies
- Authentication
- Request body
- HTTP methods

Everything ready.

---

# Why Is This Important for Testers?

Because now you can start modifying requests.

Example:

```json
"user_id":1
```

Change it to:

```json
"user_id":2
```

And this is where testing begins for:

- IDOR
- BOLA
- Broken Access Control

---

# The Most Important Mindset

# Recon Is Not Just Information Gathering

It is:

# Building Attack Hypotheses

---

# Example

You found:

```text
/api/v1/users
```

Now think:

- Is there an IDOR?
- Is authentication weak?
- Can I enumerate users?
- Does it allow mass assignment?
- Are there hidden methods?

---

# What Do We Gain From This Phase?

# 1. Mapping the Application

You understand:

- How it works
- Where the data is
- Where authentication happens
- Where admin functionality exists

---

# 2. Discovering Hidden APIs

Often the most dangerous ones.

---

# 3. Collecting Tokens

Sometimes more dangerous than vulnerabilities themselves.

---

# 4. Discovering Development Environments

Such as:

- staging
- uat
- dev

---

# 5. Discovering Documentation

Examples:

```text
/swagger
/api-docs
/redoc
/openapi.json
```

---

# 6. Identifying the Backend Technology

Examples:

- NodeJS
- Django
- Laravel
- Spring Boot

---

# Fast Professional Workflow

## 1. Run Nmap

```bash
nmap -sC -sV -p- TARGET
```

---

## 2. Open Every Port Manually

Inspect every discovered service manually.

---

## 3. Run Amass

```bash
amass enum -passive -d target.com
```

---

## 4. Filter APIs

```bash
grep api
```

---

## 5. Run Gobuster

```bash
gobuster dir -u http://target -w api.txt
```

---

## 6. Run Kiterunner

```bash
kr scan http://target
```

---

## 7. Inspect the Network Tab

Open DevTools and analyze requests.

---

## 8. Copy Requests into Postman or Burp

Replay and modify requests.

---

## 9. Start Endpoint Analysis

Begin vulnerability testing.

---

# Essential Tools You Must Master

| Tool | Purpose |
|------|----------|
| Nmap | Service discovery |
| Amass | Asset enumeration |
| Gobuster | Directory brute forcing |
| Kiterunner | API discovery |
| Burp Suite | Interception and analysis |
| Postman | API testing |
| DevTools | Request monitoring |
| jq | JSON parsing |
| httpx | Fast probing |
| ffuf | High-speed brute forcing |

---

# Additional Powerful Tools

## ffuf

Usually faster than Gobuster.

```bash
ffuf -u http://target/FUZZ -w api.txt
```

---

# httpx

For probing thousands of subdomains quickly.

https://github.com/projectdiscovery/httpx

---

# katana

An excellent crawler for extracting APIs.

https://github.com/projectdiscovery/katana

---

# hakrawler

Extracts endpoints from JavaScript files.

https://github.com/hakluke/hakrawler

---

# The Most Important Point in the Entire Field

# API Recon = 70% of Successful Testing

If you discover:

- A hidden endpoint
- A weak admin API
- An old version
- A debug API

You may find a Critical vulnerability immediately.

---

# How Does a Professional Think?

Not:

> Does an API exist?

But:

- Where is the API?
- How does it work?
- Who uses it?
- What authentication method is used?
- Are there old versions?
- Are there testing environments?
- Are there hidden parameters?
- Are there undocumented endpoints?

---

# The Next Phase After Recon

After collecting endpoints, you begin:

# Endpoint Analysis

Testing for:

- Authorization issues
- Input validation flaws
- Rate limit weaknesses
- IDOR
- Mass assignment
- BOLA
- SSRF
- RCE
- GraphQL abuse

---

# Final Professional Advice

Most beginners:

- Run a tool
- Wait for a vulnerability

A professional:

- Connects information together
- Understands application logic
- Builds attack hypotheses
- Performs manual analysis

That is the real difference.
