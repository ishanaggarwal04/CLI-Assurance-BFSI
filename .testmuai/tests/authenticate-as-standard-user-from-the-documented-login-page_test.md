---
assurance:
  id: t-1
  base: sha256:d2a200b0ad746bf62b284cf7f4d2f34c8e096e00856f3775f83a6c5ae130cd71
---
# Authenticate as standard_user from the documented login page

> Prove a valid full-access credential establishes an authenticated session and reaches the appropriate standard banking experience.

## Step 1 @verifies ac-1

Open https://qaplayground.com/bank/login in a browser, store the visible unauthenticated login page as baseline_login_state, then assert the browser URL is exactly https://qaplayground.com/bank/login.

## Step 2 @verifies ac-2, ac-3, ac-4, ac-5, ac-6, ac-7, ac-8

On the Bank Demo login page and its visible Test credentials section, enter username standard_user and password bank_sauce, use the password visibility control to reveal and then re-hide the entered password, and inspect the surrounding login controls, then assert the page shows a username field, a password field that masked the entered password before reveal, a visibility control that changes only the password visibility and not the typed value, a Remember me checkbox, a clearly labeled Sign In control, a Forgot password entry point, and credential rows for standard_user, locked_user, frozen_user, overdraft_user, slow_user, error_user, and admin_user.

## Step 3 @verifies ac-14, ac-17

Submit the standard_user credentials from the login page, then assert the unauthenticated login surface is replaced by an authenticated banking experience that corresponds to the standard user's normal/full-access view.
