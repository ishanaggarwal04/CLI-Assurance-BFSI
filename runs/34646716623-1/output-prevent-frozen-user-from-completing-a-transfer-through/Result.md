---
test: ../prevent-frozen-user-from-completing-a-transfer-through_test.md
status: passed
started: 2026-09-11T20:59:12.847Z
duration_s: 155
session_id: 9ca06ce4-774b-44c6-8778-52aed07c2df9
---

# Prevent frozen_user from completing a transfer through ordinary UI actions — Result

## Step 1 ✓ passed (24.6s)
md5: 63c1074f71b6eb5e73d932c4c5c94c42
Open https://qaplayground.com/bank/login in the browser and sign in as frozen_user with password bank_sauce until the authenticated banking experience for the frozen persona is visible.

## Step 2 ✓ passed (57.3s)
md5: 764b2a6e2d8d87a8381df8c5aa385212
In the authenticated banking experience for frozen_user, locate the visible accounts or banking overview area and store the currently displayed balances and visible transaction/activity snapshot as frozen_transfer_baseline.

## Step 3 ✓ passed (69.5s)
md5: f876878dafcae63aa135e95d3188e204
From the frozen_user banking experience, navigate to the transfer or money-movement area and attempt a transfer of 200 between any visible accounts available on that surface, then assert the transfer action is unavailable, disabled, or clearly rejected, no completed transfer is shown for frozen_user, and the displayed balances and visible transaction/activity snapshot still match frozen_transfer_baseline.
