# Lab: Unprotected Admin Functionality

## Goal
Get access to the admin panel without permission and delete the target user.

## Concepts
1. **Access Control**
2. **Broken Access Control** (Unprotected Admin Functionality)

## Solution Steps
1. Explored and browsed the application.
2. Examined the `robots.txt` file to check for hidden paths.
3. Identified the undisclosed path for the admin panel (e.g., `/administrator-panel`).
4. Navigated directly to the admin path in the browser.
5. Successfully deleted the target user (`carlos`).

## What I Have Learned
1. **Security through Obscurity fails:** Never rely on hiding sensitive links or files (like relying solely on `robots.txt` or obscure URLs) for security.
2. **Server-side Access Control is critical:** Proper access control and authorization checks must be enforced strictly on the server-side for all administrative endpoints and actions.



