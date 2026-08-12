# OWASP WebGoat – Installation Guide

## 📌 Overview

[OWASP WebGoat](https://owasp.org/www-project-webgoat/) is an intentionally vulnerable web application created by OWASP for learning and practicing web application security concepts in a safe environment.

This guide explains how to install and run WebGoat on Windows.

---

## 🛠️ Requirements

Before installing WebGoat, make sure you have:

* Windows 10/11
* Java JDK 23 or compatible Java version
* WebGoat JAR file
* Internet connection for downloading dependencies if required

> **Note:** WebGoat versions may require different Java versions. For the `webgoat-2025.3.jar` version, use a compatible recent JDK such as Java 23.

---

## 1. Install Java JDK

Download and install a Java Development Kit (JDK).

After installation, open **PowerShell** or **Command Prompt** and check:

```powershell
java --version
```

Example:

```text
java 23.x.x
```

Also check:

```powershell
javac --version
```

If Java is not recognized, configure the Java `PATH` environment variable.

---

## 2. Download WebGoat

Download the WebGoat JAR file from the official OWASP WebGoat project:

https://owasp.org/www-project-webgoat/

The downloaded file should look similar to:

```text
webgoat-2025.3.jar
```

Place the JAR file in an easy-to-access directory, for example:

```text
C:\WebGoat\
```

---

## 3. Open the WebGoat Directory

Open PowerShell or Command Prompt and navigate to the directory containing the JAR file:

```powershell
cd C:\WebGoat
```

Verify that the file exists:

```powershell
dir
```

You should see:

```text
webgoat-2025.3.jar
```

---

## 4. Start WebGoat

Run WebGoat using:

```powershell
java -Dfile.encoding=UTF-8 -Dwebgoat.port=8080 -Dwebwolf.port=9090 -jar webgoat-2025.3.jar
```

If the application starts successfully, the terminal will display startup information.

Keep this terminal window open while using WebGoat.

---

## 5. Open WebGoat

Open your browser and visit:

```text
http://127.0.0.1:8080/WebGoat/
```

You can also use:

```text
http://localhost:8080/WebGoat/
```

Create a WebGoat account and log in.

---

## 6. WebWolf

WebWolf is included with WebGoat and is used in several security exercises.

Open:

```text
http://127.0.0.1:9090/WebWolf/
```

WebWolf provides a separate environment for receiving requests, emails, files, and other data during certain WebGoat lessons.

---

## 7. Verify the Installation

The installation is successful if:

* WebGoat opens at port `8080`
* You can create/login to a WebGoat account
* WebWolf opens at port `9090`
* WebGoat lessons are visible
* The application does not show startup errors in the terminal

---

## 📁 Recommended Directory Structure

```text
C:\WebGoat\
│
└── webgoat-2025.3.jar
```

---

## ⚠️ Common Problems

### Java Version Error

If you see:

```text
UnsupportedClassVersionError
```

your Java runtime is older than the Java version used to compile WebGoat.

Check your version:

```powershell
java --version
```

Install/use a compatible JDK and make sure the correct Java executable is being used.

---

### Port 8080 Already in Use

If WebGoat cannot start because port `8080` is already being used, check which process is using it:

```powershell
netstat -ano | findstr :8080
```

You can then stop the conflicting application or configure WebGoat to use another port.

---

### Port 9090 Already in Use

Check:

```powershell
netstat -ano | findstr :9090
```

Stop the conflicting process or configure WebWolf to use another available port.

---

## 🔐 Important Security Note

WebGoat is intentionally vulnerable.

Run it **only on your local machine or an isolated lab environment**. Do not expose WebGoat directly to the public internet or an untrusted network.

WebGoat is designed for authorized security training and education.

---

## 🎯 Purpose of the Lab

WebGoat can be used to practice concepts such as:

* Cross-Site Request Forgery (CSRF)
* Cross-Site Scripting (XSS)
* SQL Injection
* Authentication vulnerabilities
* Access control
* Session management
* Security misconfigurations
* Other OWASP web application security concepts

---

## 📚 Official Resources

* OWASP WebGoat: https://owasp.org/www-project-webgoat/
* OWASP WebGoat GitHub: https://github.com/WebGoat/WebGoat

---

## ✅ Installation Complete

Once WebGoat and WebWolf are accessible through the browser, the installation is complete.

You can now begin working through the WebGoat security lessons in your local lab environment.
