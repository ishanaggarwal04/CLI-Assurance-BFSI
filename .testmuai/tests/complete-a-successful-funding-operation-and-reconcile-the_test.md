---
assurance:
  id: t-15
  base: sha256:2d67c58fb110bad9eee1238ad747907e830464e8e995f0d21dad71de4d998a48
---
# Complete a successful funding operation and reconcile the resulting balance for standard_user

> Prove that a supported authenticated user can initiate and complete funding with a valid amount, increase the targeted balance by the committed amount, and see the operation reflected in transaction history where that surface is exposed.

## Step 1

At https://qaplayground.com/bank/login, sign in as standard_user with password bank_sauce and reach the authenticated banking experience.

## Step 2 @verifies ac-47

In the authenticated banking experience, open an account view that exposes a deposit, add-funds, or equivalent balance-increase action, store that account's displayed current balance as baseline_balance, and if the same account exposes transaction or activity history store the current visible history state as baseline_history, then assert the funding action is available for that account.

## Step 3 @verifies ac-42, ac-43

On that funding surface, submit a funding amount of 200 to the same account, then assert the amount is accepted and the displayed balance for that account equals baseline_balance plus 200.

## Step 4 @verifies ac-46

If the funded account exposes transaction or activity history on the current web surface, open that account's transaction or activity history and inspect the newest visible entries, then assert a recorded funding entry for 200 on the same account is visible.
