---
test: ../block-residual-protected-banking-access-after-logout_test.md
status: passed
started: 2026-09-11T20:36:48.416Z
duration_s: 141
session_id: 000c2dea-8a5d-4c67-abe9-9f7b80980ccd
---

# Block residual protected banking access after logout — Result

## Step 1 ✓ passed (39.2s)
md5: c04df5beec9f4f24b97daf35ea96096b
Open https://qaplayground.com/bank/login in a browser, sign in as standard_user with password bank_sauce, and reach the authenticated banking dashboard or equivalent protected banking home.

## Step 2 ✓ passed (32.9s)
md5: 8a39f527e9d1caf4aa2d2a079c534829
On the authenticated banking experience, store the current session state as baseline_session_state with protected banking information and operations available to standard_user.

## Step 3 ✓ passed (61s)
md5: 6f0ee9264591b1afc291622fbe6baac0
Using the visible banking navigation, open a protected banking area that shows user-specific banking information or available banking operations, use the product's logout control to end the session, then attempt to return to that protected banking area using browser navigation and assert protected banking information or operations are not available as an authenticated experience and the prior authenticated session is no longer active.
