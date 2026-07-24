# URL-Based Access Control Can Be Circumvented

## Goal
Gain unauthorized access to the admin panel and delete the target user by bypassing URL-based access controls.

## Concepts
1. **Access Control**
2. **Broken Access Control**
3. **Privilege Escalation / Request Override**

## Solution Steps
1. Attempted to access the admin panel directly via `/admin`, which returned an **Access Denied** response.
2. Intercepted the HTTP request to `/admin` using **Burp Suite Proxy**.
3. Sent the intercepted request to **Burp Repeater**.
4. Modified the main GET request path from `/admin` to `/`.
5. Added the custom HTTP header `X-Original-URL: /admin` to the request and sent it.
6. Received an HTTP `200 OK` status code, confirming the bypass of the front-end access control.
7. Applied the same bypass in the browser/proxy to view the admin panel interface.
8. Intercepted the request used to delete the target user (`/admin/delete?username=target_user`).
9. Replaced the request path with `/?username=target_user` and added the header `X-Original-URL: /admin/delete`.
10. Sent the request and confirmed that the target user was successfully deleted.

## What I Have Learned
* **Do Not Rely Solely on Front-End/URL Inspection:** Access control rules must be consistently enforced by the back-end application logic rather than relying exclusively on proxy-level URL filtering.
* **Normalize and Validate Headers:** The back-end application should not trust user-supplied headers like `X-Original-URL` or `X-Rewrite-URL` to determine resource routing or authorization context.
