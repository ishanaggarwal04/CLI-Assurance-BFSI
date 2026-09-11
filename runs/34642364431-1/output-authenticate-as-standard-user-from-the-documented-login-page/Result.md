---
test: ../authenticate-as-standard-user-from-the-documented-login-page_test.md
status: passed
started: 2026-09-11T20:06:59.708Z
duration_s: 158
session_id: f90a84fe-7546-4590-b693-33ca180d5f4b
---

# Authenticate as standard_user from the documented login page — Result

## Step 1 ✓ passed (28.2s)
md5: 3fde6810f73ae0f9c288c4f0688817ca
Open https://qaplayground.com/bank/login in a browser, store the visible unauthenticated login page as baseline_login_state, then assert the browser URL is exactly https://qaplayground.com/bank/login.

## Step 2 ✓ passed (83.8s)
md5: c1c9b3eeac6b90c70d2b3a344556a041
On the Bank Demo login page and its visible Test credentials section, enter username standard_user and password bank_sauce, use the password visibility control to reveal and then re-hide the entered password, and inspect the surrounding login controls, then assert the page shows a username field, a password field that masked the entered password before reveal, a visibility control that changes only the password visibility and not the typed value, a Remember me checkbox, a clearly labeled Sign In control, a Forgot password entry point, and credential rows for standard_user, locked_user, frozen_user, overdraft_user, slow_user, error_user, and admin_user.

## Step 3 ✓ passed (39.3s)
md5: 393b1647374ebf0f3f97692a28a46a95
Submit the standard_user credentials from the login page, then assert the unauthenticated login surface is replaced by an authenticated banking experience that corresponds to the standard user's normal/full-access view.
