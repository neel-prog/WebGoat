# OWASP WebGoat – CSRF Labs

Hands-on exploration of **Cross-Site Request Forgery (CSRF)** vulnerabilities using **OWASP WebGoat**.

This repository documents my practical work on four CSRF-related WebGoat lessons: **3, 4, 7, and 8**.

---

## 🎯 Objective

The objective of these labs was to understand how CSRF attacks work, how forged HTTP requests can be constructed, and how browser sessions can be abused to perform actions on behalf of a user.

All testing was performed in a **local OWASP WebGoat laboratory environment**.

---

## 🧪 Lab Environment

| Component | Details |
|---|---|
| Application | OWASP WebGoat |
| Version | 2025.3 |
| Browser | Google Chrome |
| Proxy | Burp Suite |
| OS | Windows |
| Environment | Localhost |

---

# 📚 Completed Lessons

## Lesson 3 – CSRF

### Objective
Understand the basic concept of Cross-Site Request Forgery and how an attacker can create a forged request that targets a vulnerable WebGoat endpoint.

### What I practiced

- Identifying a state-changing HTTP request
- Understanding HTTP methods and parameters
- Creating a malicious HTML form
- Observing the request using Burp Suite
- Understanding how the victim's browser can send the forged request

### Status

**✅ Completed**

---

## Lesson 4 – CSRF Feedback

### Objective
Demonstrate how a forged request can be used to submit feedback to the WebGoat application.

### What I practiced

- Identifying the feedback endpoint
- Analyzing the legitimate POST request
- Creating a CSRF HTML form
- Sending attacker-controlled parameters
- Verifying the request using Burp Suite

Example target:

```text
POST /WebGoat/csrf/feedback/message