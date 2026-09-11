---
test: ../show-and-resolve-the-slow-user-loading-state-during-sign-in_test.md
status: failed
started: 2026-09-11T21:02:03.434Z
duration_s: 71
session_id: 5471a5f4-a6a1-497d-9f45-cbc90908d415
---

# Show and resolve the slow_user loading state during sign-in — Result

## Step 1 ✓ passed (8.7s)
md5: 0fb813c52d7e02442a9657f8c8ab1940
Open https://qaplayground.com/bank/login in a browser.

## Step 2 ✗ failed (59.4s)
md5: 64310291ac4b0c2cd59764584a381439
Reason: Final verification failed: "a distinguishable loading or progress state is shown while the authentication attempt is in progress" — bug verdict: Loading-state assertion ran after authentication completed [automation_bug/timing_sync, confidence 0.96]
Enter username slow_user and password bank_sauce on the Bank Demo login page and submit Sign In, then assert a distinguishable loading or progress state is shown while the authentication attempt is in progress.

## Step 3 ⏭ skipped

## Step 4 ⏭ skipped
