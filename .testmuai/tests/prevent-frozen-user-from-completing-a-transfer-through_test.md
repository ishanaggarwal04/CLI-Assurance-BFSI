---
assurance:
  id: t-11
  base: sha256:f04f67f423ee875320d29fa5f1e82c93f1ff248ad15e7109fc5750e7524a1ed4
---
# Prevent frozen_user from completing a transfer through ordinary UI actions

> Prove that the frozen persona cannot perform transfers through ordinary UI actions.

## Step 1

Open https://qaplayground.com/bank/login in the browser and sign in as frozen_user with password bank_sauce until the authenticated banking experience for the frozen persona is visible.

## Step 2

In the authenticated banking experience for frozen_user, locate the visible accounts or banking overview area and store the currently displayed balances and visible transaction/activity snapshot as frozen_transfer_baseline.

## Step 3 @verifies ac-38, ac-29, ac-31

From the frozen_user banking experience, navigate to the transfer or money-movement area and attempt a transfer of 200 between any visible accounts available on that surface, then assert the transfer action is unavailable, disabled, or clearly rejected, no completed transfer is shown for frozen_user, and the displayed balances and visible transaction/activity snapshot still match frozen_transfer_baseline.
