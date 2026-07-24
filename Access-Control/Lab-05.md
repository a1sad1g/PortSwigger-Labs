# User ID Controlled by Request Parameter

## Goal
Retrieve sensitive information (such as API keys) belonging to other users by manipulating the user ID parameter.

## Concepts
1. **Access Control**
2. **Broken Access Control**
3. **Horizontal Privilege Escalation:** User ID controlled by request parameter (IDOR).

## Solution Steps
1. Browsed and explored the login page.
2. Logged into the account.
3. Intercepted the HTTP request to the account page using **Burp Suite Proxy**.
4. Modified the `id` parameter value (e.g., `id=username`) to target another user's ID.
5. Forwarded the request and successfully retrieved sensitive data for that user.

## What I Have Learned
1. **Never trust client-side request parameters for user identification:** Resource ownership must be validated based on the user's active session, not user-supplied request parameters.
2. **Implement Session-Based Authorization:** The server must strictly verify that the authenticated session user has permission to access the requested resource ID.
