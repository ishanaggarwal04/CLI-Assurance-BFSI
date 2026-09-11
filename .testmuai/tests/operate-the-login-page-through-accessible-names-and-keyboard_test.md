---
assurance:
  id: t-6
  base: sha256:acf7ef400f24b2a6910b5785c909467a4ec1dd60c26a0a5f946633d86df252fd
---
# Operate the login page through accessible names and keyboard input

> Prove the username and password fields expose accessible names, the password visibility control has an understandable accessible name, and Remember me, Sign In, and Forgot password are keyboard operable.

## Step 1

Open https://qaplayground.com/bank/login in a browser.

## Step 2 @verifies ac-9

Inspect the username and password fields on the Bank Demo login page through the browser's accessibility information, then assert each field exposes an accessible label or equivalent accessible name.

## Step 3 @verifies ac-10

Inspect the password visibility control through the browser's accessibility information, then assert it exposes an understandable accessible name.

## Step 4 @verifies ac-11

Using keyboard-only interaction on the Bank Demo login page, move to the Remember me checkbox and toggle it, then assert the checkbox state changes in response to the keyboard input.

## Step 5 @verifies ac-11

Using keyboard-only interaction on the Bank Demo login page, activate the Forgot password entry point, then assert it opens a forgot-password destination or recovery flow.

## Step 6 @verifies ac-11

Return to the Bank Demo login page, enter username standard_user and password bank_sauce, activate Sign In from the keyboard, then assert the authenticated banking experience opens from the keyboard-triggered submission.
