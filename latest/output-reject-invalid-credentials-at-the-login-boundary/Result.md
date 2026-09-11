---
test: ../reject-invalid-credentials-at-the-login-boundary_test.md
status: passed
started: 2026-09-11T20:13:03.935Z
duration_s: 55
session_id: 4a7fd828-027e-4af6-88c9-c1d31849513b
---

# Reject invalid credentials at the login boundary — Result

## Step 1 ✓ passed (9.8s)
md5: 0fb813c52d7e02442a9657f8c8ab1940
Open https://qaplayground.com/bank/login in a browser.

## Step 2 ✓ passed (41.1s)
md5: 23ab9cb20ab8b7f0740c49f01a0d391c
Enter username {{invalid_username}} and password {{invalid_password}} on the Bank Demo login page and submit Sign In, then assert an understandable failure state is shown and an authenticated banking experience is not available.
