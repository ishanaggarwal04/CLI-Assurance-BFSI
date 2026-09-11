---
assurance:
  id: t-5
  base: sha256:1dd2d5843f47634592585dd0d51a88ea8145314bd15b4c386dc52585030fe29b
---
# Show and resolve the slow_user loading state during sign-in

> Prove the slow-loading persona shows an understandable in-progress state during authentication and eventually resolves to its intended post-login experience.

## Step 1

Open https://qaplayground.com/bank/login in a browser.

## Step 2 @verifies ac-20

Enter username slow_user and password bank_sauce on the Bank Demo login page and submit Sign In, then assert a distinguishable loading or progress state is shown while the authentication attempt is in progress.

## Step 3

On the displayed slow-user loading state, store the visible in-progress sign-in view as baseline_slow_loading_state.

## Step 4 @verifies ac-21

Allow the in-progress slow_user sign-in to complete from the displayed loading state, then assert the loading state resolves into the intended internally consistent authenticated banking experience for the signed-in user.
