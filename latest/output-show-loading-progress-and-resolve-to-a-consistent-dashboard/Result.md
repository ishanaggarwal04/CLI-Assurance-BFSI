---
test: ../show-loading-progress-and-resolve-to-a-consistent-dashboard_test.md
status: passed
started: 2026-09-11T20:15:59.296Z
duration_s: 139
session_id: 3ab1ca1d-869b-44c3-ad67-969d5fac03bc
---

# Show loading progress and resolve to a consistent dashboard for slow_user — Result

## Step 1 ✓ passed (40.8s)
md5: 09fdfe674857cef9b8481da610e1621f
On https://qaplayground.com/bank/login, ensure the Bank Demo is at the login page and capture baseline: successful active-user login submitted from the Bank Demo login page.

## Step 2 ✓ passed (48.5s)
md5: 558118975cc19931dff840c55b6547f3
On the Bank Demo login page, sign in with username slow_user and password bank_sauce, and when the banking experience enters its intermediate loading state capture baseline: slow_user banking experience is in a loading state, then assert a user-understandable loading or progress indication is shown while the overview is still resolving.

## Step 3 ✓ passed (46.8s)
md5: c41b5e563bba85a59e2d1dee49f75880
Allow the slow_user banking experience to finish resolving without re-submitting the login, then assert it resolves to the authenticated experience appropriate to slow_user with persona/state still matching that user and with internally consistent banking state.
