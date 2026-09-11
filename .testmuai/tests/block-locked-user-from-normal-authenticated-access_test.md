---
assurance:
  id: t-3
  base: sha256:8e61e52d2c04abd43bbf5007b4784ab5b8065e1be87b79b691acba71aa1e833d
---
# Block locked_user from normal authenticated access

> Prove the locked persona receives a clear locked-state outcome and is not treated as a normal active session.

## Step 1

Open https://qaplayground.com/bank/login in a browser.

## Step 2 @verifies ac-12, ac-18

Enter username locked_user and password bank_sauce on the Bank Demo login page and submit Sign In, then assert a clear locked-state outcome is shown and the application does not grant the same normal authenticated banking access as standard_user.
