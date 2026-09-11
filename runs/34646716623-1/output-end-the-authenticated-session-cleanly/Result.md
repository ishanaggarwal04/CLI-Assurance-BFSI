---
test: ../end-the-authenticated-session-cleanly_test.md
status: passed
started: 2026-09-11T20:57:58.044Z
duration_s: 103
session_id: 31ef95d2-c66a-483b-9413-e29ef1141975
---

# End the authenticated session cleanly — Result

## Step 1 ✓ passed (23.7s)
md5: c04df5beec9f4f24b97daf35ea96096b
Open https://qaplayground.com/bank/login in a browser, sign in as standard_user with password bank_sauce, and reach the authenticated banking dashboard or equivalent protected banking home.

## Step 2 ✓ passed (43.9s)
md5: 57e6a6b832b9cde0013baabdf8bb1b2a
On the authenticated banking experience, store the current session state as baseline_session_state showing the product is in the Authenticated state for standard_user.

## Step 3 ✓ passed (30.8s)
md5: f45144f714c0bba6efa56587385350f9
From the authenticated banking experience, use the product's logout control to end the session, then assert only public or login functionality is available and the authenticated banking experience is no longer active.
