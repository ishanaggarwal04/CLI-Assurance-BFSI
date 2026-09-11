---
assurance:
  id: t-2
  base: sha256:7da28b09dabfa0db0e6dedfa5cd97c85d4a2c0869c1a7c2433754f680b884448
---
# Reject invalid credentials at the login boundary

> Prove invalid credentials do not grant access and produce an understandable failure state instead of an authenticated session.

## Step 1

Open https://qaplayground.com/bank/login in a browser.

## Step 2 @verifies ac-13, ac-19

Enter username {{invalid_username}} and password {{invalid_password}} on the Bank Demo login page and submit Sign In, then assert an understandable failure state is shown and an authenticated banking experience is not available.
