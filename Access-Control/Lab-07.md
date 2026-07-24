# User ID Controlled by Request Parameter with Data Leakage in redirect

## Goal
Access sensitive information belonging to another user.

## Concepts
1. **Access Control:** Enforcing permissions on sensitive endpoints.
2. **Broken Access Control / IDOR:** Unvalidated parameter references leading to unauthorized data disclosure.
3. **Horizontal Privilege Escalation:** Accessing resource data of a peer user at the same permission level.

## Solution Steps
1. Navigated to the account page.
2. Intercepted the HTTP account request using **Burp Suite Proxy**.
3. Changed the parameter from `id=my_name` to `id=target_name`.
4. Analyzed the HTTP response: although a redirect status was returned, the response body contained the target user's sensitive information.

## Key Takeaways
* **Never trust client-side parameters:** Always authorize requested resources server-side using the active session token.
* **Inspect Redirect Responses:** Do not rely on HTTP redirect status codes (e.g., 302) for security; ensure sensitive data is not rendered in the response body during redirects.
