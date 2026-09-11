---
test: ../end-the-authenticated-session-cleanly_test.md
status: passed
started: 2026-09-11T20:38:37.779Z
duration_s: 102
session_id: c18b2aab-7700-448c-8eb6-36c615968e76
---

# End the authenticated session cleanly — Result

## Step 1 ✓ passed (23.6s)
md5: c04df5beec9f4f24b97daf35ea96096b
Open https://qaplayground.com/bank/login in a browser, sign in as standard_user with password bank_sauce, and reach the authenticated banking dashboard or equivalent protected banking home.

## Step 2 ✓ passed (34.9s)
md5: 57e6a6b832b9cde0013baabdf8bb1b2a
On the authenticated banking experience, store the current session state as baseline_session_state showing the product is in the Authenticated state for standard_user.

## Step 3 ✓ passed (40s)
md5: f45144f714c0bba6efa56587385350f9
From the authenticated banking experience, use the product's logout control to end the session, then assert only public or login functionality is available and the authenticated banking experience is no longer active.
