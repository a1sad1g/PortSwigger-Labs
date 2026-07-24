# Insecure Direct Object References (IDOR)

## Goal
Gain access to another user's account by extracting credentials from leaked chat logs.

## Concepts
1. **Access Control**
2. **Broken Access Control (IDOR)**
3. **Privilege Escalation / Data Exposure**

## Solution Steps
1. Logged into my account and opened the live chat feature.
2. Triggered the option to download the chat transcript (`2.txt`).
3. Intercepted or modified the request, changing the filename/ID parameter from `2.txt` to `1.txt`.
4. Opened the downloaded file (`1.txt`) and found a chat history containing the target user's password.
5. Logged out of my account and successfully logged into the target user's account using the retrieved credentials.

## What I Have Learned
* **Enforce Strict Authorization on Static/Generated Files:** The server must verify if the current user session owns the requested transcript file (e.g., `1.txt`) before granting download access.
* **Do Not Rely on Sequential IDs:** Sequential file names (like `1.txt`, `2.txt`) make enumeration trivial; static resources containing sensitive data should use unpredictable access controls and authorization checks.

