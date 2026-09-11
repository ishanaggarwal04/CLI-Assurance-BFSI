---
assurance:
  id: t-8
  base: sha256:6d0c50aca5dde423b0f7b4acdb5696a9871cbf95e9995e7744d660c70789f68d
---
# End the authenticated session cleanly

> Prove that a logged-in banking user can end the current authenticated session and leave the authenticated product state.

## Step 1

Open https://qaplayground.com/bank/login in a browser, sign in as standard_user with password bank_sauce, and reach the authenticated banking dashboard or equivalent protected banking home.

## Step 2

On the authenticated banking experience, store the current session state as baseline_session_state showing the product is in the Authenticated state for standard_user.

## Step 3 @verifies ac-22

From the authenticated banking experience, use the product's logout control to end the session, then assert only public or login functionality is available and the authenticated banking experience is no longer active.
