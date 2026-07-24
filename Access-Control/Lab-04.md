# User Role Can Be Modified in User Profile

## Goal
Gain access to the admin panel by modifying the user role parameter during a profile update.

## Concepts
1. **Access Control**
2. **Broken Access Control:** Mass Assignment / Role modification via user profile API.

## Solution Steps
1. Browsed and explored the login page.
2. Logged into the account and updated the profile email.
3. Intercepted the email update HTTP request using **Burp Suite Proxy**.
4. Sent the request to **Burp Repeater** and inspected the JSON structure.
5. Identified that adding or modifying the `"roleid": 2` parameter in the JSON request payload assigned admin permissions to the account.
6. Accessed the admin panel and successfully deleted the target user.

## What I Have Learned
1. **Never trust client-side data:** Do not rely on parameters sent in the HTTP request body or headers (JSON, parameters, cookies) to establish user permissions.
2. **Prevent Mass Assignment:** Enforce robust server-side validation to ensure clients can only modify authorized parameters in their profile updates.
