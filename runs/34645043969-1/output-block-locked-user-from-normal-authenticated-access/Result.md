---
test: ../block-locked-user-from-normal-authenticated-access_test.md
status: passed
started: 2026-09-11T20:36:56.584Z
duration_s: 57
session_id: 1ce33de7-aa55-401b-8b65-0dea3f381816
---

# Block locked_user from normal authenticated access — Result

## Step 1 ✓ passed (10.8s)
md5: 0fb813c52d7e02442a9657f8c8ab1940
Open https://qaplayground.com/bank/login in a browser.

## Step 2 ✓ passed (38.4s)
md5: a2b282dbb2e594737f027fc5b0817aeb
Enter username locked_user and password bank_sauce on the Bank Demo login page and submit Sign In, then assert a clear locked-state outcome is shown and the application does not grant the same normal authenticated banking access as standard_user.
