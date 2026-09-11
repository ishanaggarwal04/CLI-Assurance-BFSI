---
assurance:
  id: t-14
  base: sha256:bd743d194297951404b2b5a63ba8d4d610b2557fa5233cca9c72405f6f909b8f
---
# Reject a non-numeric transfer amount without creating partial transfer state

> Prove that an invalid formatted amount is not silently accepted as a successful transfer.

## Step 1

Open https://qaplayground.com/bank/login in the browser and sign in as standard_user with password bank_sauce until the authenticated banking experience is visible.

## Step 2 @verifies ac-35, ac-36, ac-37

In the authenticated banking experience for standard_user, open the transfer or money-movement form and locate the source account selector, destination account selector, and monetary amount input, then assert all three transfer inputs are present.

## Step 3

In the accounts and transaction/activity areas for the accounts named savings1000 and checkings500, store the current displayed source balance, destination balance, and relevant visible history snapshot as non_numeric_transfer_baseline.

## Step 4 @verifies ac-41, ac-34, ac-31

Using the transfer form, enter abc as the amount for a transfer from the account named savings1000 to the account named checkings500 and attempt to submit it, then assert understandable feedback associated with the transfer operation is shown, no successful transfer completion is shown, and the displayed balances and visible transaction/activity snapshot still match non_numeric_transfer_baseline.
