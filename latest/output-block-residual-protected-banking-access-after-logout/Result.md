---
test: ../block-residual-protected-banking-access-after-logout_test.md
status: passed
started: 2026-09-11T20:07:03.063Z
duration_s: 155
session_id: 1a13f5ae-c76b-45a0-81df-5c2a5e2ef542
---

# Block residual protected banking access after logout — Result

## Step 1 ✓ passed (44.3s)
md5: c04df5beec9f4f24b97daf35ea96096b
Open https://qaplayground.com/bank/login in a browser, sign in as standard_user with password bank_sauce, and reach the authenticated banking dashboard or equivalent protected banking home.

## Step 2 ✓ passed (50.3s)
md5: 8a39f527e9d1caf4aa2d2a079c534829
On the authenticated banking experience, store the current session state as baseline_session_state with protected banking information and operations available to standard_user.

## Step 3 ✓ passed (54.8s)
md5: 6f0ee9264591b1afc291622fbe6baac0
Using the visible banking navigation, open a protected banking area that shows user-specific banking information or available banking operations, use the product's logout control to end the session, then attempt to return to that protected banking area using browser navigation and assert protected banking information or operations are not available as an authenticated experience and the prior authenticated session is no longer active.
