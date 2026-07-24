# Unprotected Admin Functionality with Unpredictable URL

## Goal
Gain access to the admin panel without proper authorization and delete the target user.

## Concepts
1. **Access Control:** Unprotected admin functionality with an unpredictable URL.
2. **Broken Access Control**

## Solution Steps
1. Explored and browsed the main application.
2. Intercepted the home page HTTP request using **Burp Suite Proxy**.
3. Sent the request to **Burp Repeater** to inspect the full HTTP response.
4. Found the disclosure of the unpredictable admin URL hidden inside the HTTP response (e.g., in inline JavaScript code).
5. Navigated directly to the extracted admin path in the browser.
6. Successfully deleted the target user.

## What I Have Learned
1. **Never leak sensitive endpoints in client-side responses:** Obscuring admin URLs is not a security measure (Security through Obscurity) if they are revealed in source code or response bodies.
2. **Implement server-side authorization:** Always enforce access control checks on the server side regardless of how hidden or unpredictable the URL is.
