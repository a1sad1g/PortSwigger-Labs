# User ID Controlled by Request Parameter with Password Disclosure

## Goal
Gain unauthorized access to the administrator account using disclosed credentials.

## Concepts
1. **Access Control**
2. **Broken Access Control (IDOR)**
3. **Vertical Privilege Escalation:** Elevating privileges from a standard user to an administrator due to improper authorization checks.

## Solution Steps
1. Logged into my standard user account.
2. Intercepted the account page HTTP request using **Burp Suite Proxy**.
3. Sent the request to **Burp Repeater** for analysis and manipulation.
4. Changed the parameter from `id=my_name` to `id=administrator`.
5. Analyzed the response body and identified the plaintext administrator password.
6. Logged out of my account and logged into the `administrator` account using the retrieved password.
7. Accessed the Admin Panel and successfully deleted the target user.

## Key Takeaways
* **Never trust client-side input:** The backend must independently verify if the authenticated session has permission to access the requested user ID.
* **Avoid Sensitive Data Exposure:** Sensitive fields (such as passwords or secret tokens) should never be rendered in HTTP response bodies, even for profile pages.
