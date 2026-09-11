---
assurance:
  id: t-16
  base: sha256:6ae9e88b6a993dbcea41c338c16d5f8510b11ae0533cb0f2f22b53660b798f3b
---
# Reject a non-numeric funding amount without changing balance or transaction history

> Prove that a funding attempt with a non-numeric amount is rejected and does not create a false balance change or a completed transaction record.

## Step 1

At https://qaplayground.com/bank/login, sign in as standard_user with password bank_sauce and reach the authenticated banking experience.

## Step 2 @verifies ac-47

In the authenticated banking experience, open an account view that exposes a deposit, add-funds, or equivalent balance-increase action, store that account's displayed current balance as baseline_balance, and if the same account exposes transaction or activity history store the current visible history state as baseline_history, then assert the funding action is available for that account.

## Step 3 @verifies ac-42, ac-44

On that funding surface, attempt to submit a funding amount of abc to the same account, then assert the application rejects the input with visible validation or error feedback and the displayed balance for that account remains baseline_balance.

## Step 4 @verifies ac-45

If the same account exposes transaction or activity history on the current web surface, inspect the latest visible activity after the rejected submission, then assert no completed funding record created by that rejected attempt is shown.
