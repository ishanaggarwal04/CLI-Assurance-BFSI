---
test: ../operate-the-login-page-through-accessible-names-and-keyboard_test.md
status: passed
started: 2026-09-11T20:39:27.342Z
duration_s: 248
session_id: 6ef721fd-8052-41dd-b7ad-992719c9f1b9
---

# Operate the login page through accessible names and keyboard input — Result

## Step 1 ✓ passed (7.9s)
md5: 0fb813c52d7e02442a9657f8c8ab1940
Open https://qaplayground.com/bank/login in a browser.

## Step 2 ✓ passed (21.9s)
md5: 4f5443b060e0fd348836f36ec3ad6a63
Inspect the username and password fields on the Bank Demo login page through the browser's accessibility information, then assert each field exposes an accessible label or equivalent accessible name.

## Step 3 ✓ passed (27.6s)
md5: 9c00cbebae931141c9b2ed95697cff8b
Inspect the password visibility control through the browser's accessibility information, then assert it exposes an understandable accessible name.

## Step 4 ✓ passed (85.6s)
md5: 0321ab04db0705f03cc3e0f9f0aa03d6
Using keyboard-only interaction on the Bank Demo login page, move to the Remember me checkbox and toggle it, then assert the checkbox state changes in response to the keyboard input.

## Step 5 ✓ passed (53s)
md5: 5f8e9c19723bbaf2ec2ac22c7053b938
Using keyboard-only interaction on the Bank Demo login page, activate the Forgot password entry point, then assert it opens a forgot-password destination or recovery flow.

## Step 6 ✓ passed (48.3s)
md5: a2526a9b283172a446e012a07fbb1b9a
Return to the Bank Demo login page, enter username standard_user and password bank_sauce, activate Sign In from the keyboard, then assert the authenticated banking experience opens from the keyboard-triggered submission.
