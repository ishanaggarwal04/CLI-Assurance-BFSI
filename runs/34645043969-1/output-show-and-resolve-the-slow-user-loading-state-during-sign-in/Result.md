---
test: ../show-and-resolve-the-slow-user-loading-state-during-sign-in_test.md
status: passed
started: 2026-09-11T20:42:55.823Z
duration_s: 109
session_id: f04e58c2-8111-421a-ada3-5fadac9214ab
---

# Show and resolve the slow_user loading state during sign-in — Result

## Step 1 ✓ passed (7.1s)
md5: 0fb813c52d7e02442a9657f8c8ab1940
Open https://qaplayground.com/bank/login in a browser.

## Step 2 ✓ passed (28.4s)
md5: 64310291ac4b0c2cd59764584a381439
Enter username slow_user and password bank_sauce on the Bank Demo login page and submit Sign In, then assert a distinguishable loading or progress state is shown while the authentication attempt is in progress.

## Step 3 ✓ passed (34.5s)
md5: dcc31b277bc5ef5a41867ac05fed68bc
On the displayed slow-user loading state, store the visible in-progress sign-in view as baseline_slow_loading_state.

## Step 4 ✓ passed (35.1s)
md5: f1322edfa2b6bdb5f1e79ba7a84d826d
Allow the in-progress slow_user sign-in to complete from the displayed loading state, then assert the loading state resolves into the intended internally consistent authenticated banking experience for the signed-in user.
