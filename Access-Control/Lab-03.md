# User Role Controlled by Request Parameter

## Goal
Gain access to the admin panel and delete the target user by manipulating the user role parameter.

## Concepts
1. **Access Control**
2. **Broken Access Control:** User role controlled by request parameter / cookie.

## Solution Steps
1. Browsed and explored the login page.
2. Logged into the account and intercepted the request using **Burp Suite Proxy**.
3. Located the cookie/parameter set to `Admin=false` (or `Admin=0`) and modified its value to `Admin=true`.
4. Forwarded the modified request to bypass the restriction, accessed the admin panel, and deleted the target user.

## What I Have Learned
1. **Never trust client-side data for authorization:** Security control mechanisms must not rely on parameters or cookies that can be manipulated by the user.
2. **Server-side role verification:** User privileges and roles must be validated strictly on the server side using securely managed session states.
