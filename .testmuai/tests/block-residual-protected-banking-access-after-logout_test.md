---
assurance:
  id: t-7
  base: sha256:be8ed512ba10ec593dad9ce978201b7c4381078704065f994563cad763c3bb91
---
# Block residual protected banking access after logout

> Prove that a page or control reached while authenticated does not remain usable as authenticated banking access after the user logs out and returns to previously visited protected content.

## Step 1

Open https://qaplayground.com/bank/login in a browser, sign in as standard_user with password bank_sauce, and reach the authenticated banking dashboard or equivalent protected banking home.

## Step 2

On the authenticated banking experience, store the current session state as baseline_session_state with protected banking information and operations available to standard_user.

## Step 3 @verifies ac-23, ac-22

Using the visible banking navigation, open a protected banking area that shows user-specific banking information or available banking operations, use the product's logout control to end the session, then attempt to return to that protected banking area using browser navigation and assert protected banking information or operations are not available as an authenticated experience and the prior authenticated session is no longer active.
