---
test: ../reject-a-non-numeric-transfer-amount-without-creating_test.md
status: passed
started: 2026-09-11T20:12:58.124Z
duration_s: 209
session_id: 1c6d0bb9-6a23-45ea-b8b7-38f3d25cf280
---

# Reject a non-numeric transfer amount without creating partial transfer state — Result

## Step 1 ✓ passed (24.4s)
md5: c4dc508a6d5cc977e92f885d537c6d6f
Open https://qaplayground.com/bank/login in the browser and sign in as standard_user with password bank_sauce until the authenticated banking experience is visible.

## Step 2 ✓ passed (33.7s)
md5: 806e9500aa4e01aae3f9e0576e20a240
In the authenticated banking experience for standard_user, open the transfer or money-movement form and locate the source account selector, destination account selector, and monetary amount input, then assert all three transfer inputs are present.

## Step 3 ✓ passed (52.3s)
md5: ad727fa8053ff6756a436ed906852261
In the accounts and transaction/activity areas for the accounts named savings1000 and checkings500, store the current displayed source balance, destination balance, and relevant visible history snapshot as non_numeric_transfer_baseline.

## Step 4 ✓ passed (94.3s)
md5: e33b643903c764897192b4a3f774fd66
Using the transfer form, enter abc as the amount for a transfer from the account named savings1000 to the account named checkings500 and attempt to submit it, then assert understandable feedback associated with the transfer operation is shown, no successful transfer completion is shown, and the displayed balances and visible transaction/activity snapshot still match non_numeric_transfer_baseline.
