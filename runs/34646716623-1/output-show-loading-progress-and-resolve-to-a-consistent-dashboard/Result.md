---
test: ../show-loading-progress-and-resolve-to-a-consistent-dashboard_test.md
status: failed
started: 2026-09-11T21:03:32.669Z
duration_s: 220
session_id: 5f02980a-c03f-4f22-884e-a83410df852f
---

# Show loading progress and resolve to a consistent dashboard for slow_user — Result

## Step 1 ✓ passed (58s)
md5: 09fdfe674857cef9b8481da610e1621f
On https://qaplayground.com/bank/login, ensure the Bank Demo is at the login page and capture baseline: successful active-user login submitted from the Bank Demo login page.

## Step 2 ✗ failed (158.4s)
md5: 558118975cc19931dff840c55b6547f3
Reason: Final verification failed: "a user-understandable loading or progress indication is shown while the overview is still resolving." — bug verdict: Dashboard loading state lacks a user-understandable progress indicator [application_issue/ui_state_mismatch, confidence 0.93]
On the Bank Demo login page, sign in with username slow_user and password bank_sauce, and when the banking experience enters its intermediate loading state capture baseline: slow_user banking experience is in a loading state, then assert a user-understandable loading or progress indication is shown while the overview is still resolving.

## Step 3 ⏭ skipped
