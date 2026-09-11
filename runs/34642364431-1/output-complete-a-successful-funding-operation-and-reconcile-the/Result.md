---
test: ../complete-a-successful-funding-operation-and-reconcile-the_test.md
status: passed
started: 2026-09-11T20:07:02.732Z
duration_s: 398
session_id: 14bed66e-15bb-425e-82d5-d2f48aaff72d
---

# Complete a successful funding operation and reconcile the resulting balance for standard_user — Result

## Step 1 ✓ passed (27s)
md5: c1ff229b0314abcf6630dade0a5e480d
At https://qaplayground.com/bank/login, sign in as standard_user with password bank_sauce and reach the authenticated banking experience.

## Step 2 ✓ passed (216.4s)
md5: 9ff7786ae62b3cf6c24d39bb1dcbad7e
In the authenticated banking experience, open an account view that exposes a deposit, add-funds, or equivalent balance-increase action, store that account's displayed current balance as baseline_balance, and if the same account exposes transaction or activity history store the current visible history state as baseline_history, then assert the funding action is available for that account.

## Step 3 ✓ passed (84.3s)
md5: 7b5337fab77d8ba37b85c2099c52d61a
On that funding surface, submit a funding amount of 200 to the same account, then assert the amount is accepted and the displayed balance for that account equals baseline_balance plus 200.

## Step 4 ✓ passed (65.1s)
md5: 33965898c4e556448c6df12a6a09a3e7
If the funded account exposes transaction or activity history on the current web surface, open that account's transaction or activity history and inspect the newest visible entries, then assert a recorded funding entry for 200 on the same account is visible.
