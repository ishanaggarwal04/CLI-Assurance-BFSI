---
test: ../block-locked-user-from-normal-authenticated-access_test.md
status: passed
started: 2026-09-11T20:07:00.419Z
duration_s: 62
session_id: 23db8640-1a44-4fa9-9121-ca3c823efeb0
---

# Block locked_user from normal authenticated access — Result

## Step 1 ✓ passed (9.9s)
md5: 0fb813c52d7e02442a9657f8c8ab1940
Open https://qaplayground.com/bank/login in a browser.

## Step 2 ✓ passed (46.3s)
md5: a2b282dbb2e594737f027fc5b0817aeb
Enter username locked_user and password bank_sauce on the Bank Demo login page and submit Sign In, then assert a clear locked-state outcome is shown and the application does not grant the same normal authenticated banking access as standard_user.
