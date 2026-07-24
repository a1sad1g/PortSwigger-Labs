# User ID Controlled by Request parameter, with unpredictable users IDs (IDOR)

## Goal
Access sensitive information belonging to other users.

## Concepts
1. **Access Control**
2. **Broken Access Control**
3. **Horizontal Privilege Escalation:** Accessing another user's account data with the same privilege level via manipulated URL parameters.

## Solution Steps
1. Browsed and explored the homepage posts.
2. Located the target user's profile/post and clicked their username link.
3. Identified the target user's identifier (`username_id`) in the URL parameter.
4. Logged into my own account and intercepted the account request using **Burp Suite Proxy**.
5. Replaced `id=my_id` with `id=username_id` in the request body/parameter and forwarded it.
6. Successfully viewed sensitive information for the target user.

## What I have learned
* **Never trust client-side parameters:** The server must independently validate all user-supplied input against the active session.
* **Session-based Access Control:** Resource ownership must always be verified on the server side using the authenticated session context.
