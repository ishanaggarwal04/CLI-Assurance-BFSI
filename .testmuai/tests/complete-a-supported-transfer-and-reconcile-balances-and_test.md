---
assurance:
  id: t-12
  base: sha256:eef77b6ae6aaf6b3304c823b0c3282e2876144cc2e0cd857250bb07a8258e9bf
---
# Complete a supported transfer and reconcile balances and history for standard_user

> Prove that a permitted authenticated user can complete a supported transfer and see consistent balance and history updates.

## Step 1

Open https://qaplayground.com/bank/login in the browser and sign in as standard_user with password bank_sauce until the authenticated banking experience is visible.

## Step 2 @verifies ac-35, ac-36, ac-37

In the authenticated banking experience for standard_user, open the transfer or money-movement form and locate the source account selector, destination account selector, and monetary amount input, then assert all three transfer inputs are present.

## Step 3

In the accounts and transaction/activity areas for the accounts named savings1000 and checkings500, store the current displayed source balance, destination balance, and relevant visible history snapshot as successful_transfer_baseline.

## Step 4 @verifies ac-39, ac-32

Using the transfer form, move 200 from the account named savings1000 to the account named checkings500 and submit the transfer, then assert clear user-visible success feedback is shown and the displayed source and destination balances update consistently with that committed transfer.

## Step 5 @verifies ac-33

Open the transaction or activity history view exposed for the authenticated banking experience and inspect the entries relevant to savings1000 and checkings500, then assert a history record for the completed 200 transfer is present.
