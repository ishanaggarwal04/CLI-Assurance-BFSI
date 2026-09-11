---
test: ../show-loading-progress-and-resolve-to-a-consistent-dashboard_test.md
status: passed
started: 2026-09-11T20:44:57.581Z
duration_s: 206
session_id: 2cf2e3b3-54b2-451c-b9b9-4d5fe32192a1
---

# Show loading progress and resolve to a consistent dashboard for slow_user — Result

## Step 1 ✓ passed (60.8s)
md5: 09fdfe674857cef9b8481da610e1621f
On https://qaplayground.com/bank/login, ensure the Bank Demo is at the login page and capture baseline: successful active-user login submitted from the Bank Demo login page.

## Step 2 ✓ passed (85.4s)
md5: 558118975cc19931dff840c55b6547f3
On the Bank Demo login page, sign in with username slow_user and password bank_sauce, and when the banking experience enters its intermediate loading state capture baseline: slow_user banking experience is in a loading state, then assert a user-understandable loading or progress indication is shown while the overview is still resolving.

## Step 3 ✓ passed (56.1s)
md5: c41b5e563bba85a59e2d1dee49f75880
Allow the slow_user banking experience to finish resolving without re-submitting the login, then assert it resolves to the authenticated experience appropriate to slow_user with persona/state still matching that user and with internally consistent banking state.
