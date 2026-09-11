---
test: ../reject-a-non-numeric-funding-amount-without-changing-balance_test.md
status: passed
started: 2026-09-11T20:13:13.470Z
duration_s: 396
session_id: 5bf6058b-ad2f-43fd-b89a-be1cb618026f
---

# Reject a non-numeric funding amount without changing balance or transaction history — Result

## Step 1 ✓ passed (28.7s)
md5: c1ff229b0314abcf6630dade0a5e480d
At https://qaplayground.com/bank/login, sign in as standard_user with password bank_sauce and reach the authenticated banking experience.

## Step 2 ✓ passed (158.7s)
md5: 9ff7786ae62b3cf6c24d39bb1dcbad7e
In the authenticated banking experience, open an account view that exposes a deposit, add-funds, or equivalent balance-increase action, store that account's displayed current balance as baseline_balance, and if the same account exposes transaction or activity history store the current visible history state as baseline_history, then assert the funding action is available for that account.

## Step 3 ✓ passed (136.4s)
md5: 497d164d99eacc6d28c15ce28540c210
On that funding surface, attempt to submit a funding amount of abc to the same account, then assert the application rejects the input with visible validation or error feedback and the displayed balance for that account remains baseline_balance.

## Step 4 ✓ passed (69.2s)
md5: 8bf960905e97d0d596638ccb3e859fe0
If the same account exposes transaction or activity history on the current web surface, inspect the latest visible activity after the rejected submission, then assert no completed funding record created by that rejected attempt is shown.
