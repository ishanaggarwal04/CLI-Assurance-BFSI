---
assurance:
  id: t-13
  base: sha256:ddc3a2e5a1e9c591741d1fbe0edeb5b7533b52d8e6fac31494a050c7c6a435e0
---
# Reject a zero transfer amount without creating partial transfer state

> Prove that a non-positive boundary amount is not silently accepted as a successful transfer.

## Step 1

Open https://qaplayground.com/bank/login in the browser and sign in as standard_user with password bank_sauce until the authenticated banking experience is visible.

## Step 2 @verifies ac-35, ac-36, ac-37

In the authenticated banking experience for standard_user, open the transfer or money-movement form and locate the source account selector, destination account selector, and monetary amount input, then assert all three transfer inputs are present.

## Step 3

In the accounts and transaction/activity areas for the accounts named savings1000 and checkings500, store the current displayed source balance, destination balance, and relevant visible history snapshot as zero_transfer_baseline.

## Step 4 @verifies ac-40, ac-34, ac-31

Using the transfer form, attempt to move 0 from the account named savings1000 to the account named checkings500 and submit the transfer, then assert understandable feedback associated with the transfer operation is shown, no successful transfer completion is shown, and the displayed balances and visible transaction/activity snapshot still match zero_transfer_baseline.
