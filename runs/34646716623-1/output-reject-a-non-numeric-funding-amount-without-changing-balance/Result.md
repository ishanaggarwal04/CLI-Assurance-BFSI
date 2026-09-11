---
test: ../reject-a-non-numeric-funding-amount-without-changing-balance_test.md
status: failed
started: 2026-09-11T21:00:01.390Z
duration_s: 196
session_id: 77cc00b2-3aa6-4d87-911e-f41ed609e4cc
---

# Reject a non-numeric funding amount without changing balance or transaction history — Result

## Step 1 ✓ passed (23.5s)
md5: c1ff229b0314abcf6630dade0a5e480d
At https://qaplayground.com/bank/login, sign in as standard_user with password bank_sauce and reach the authenticated banking experience.

## Step 2 ✗ failed (169.2s)
md5: 9ff7786ae62b3cf6c24d39bb1dcbad7e
Reason: Final verification failed: "the funding action is available for that account" — bug verdict: Funding-action assertion checks the wrong page [automation_bug/agent_misstep, confidence 0.90]
In the authenticated banking experience, open an account view that exposes a deposit, add-funds, or equivalent balance-increase action, store that account's displayed current balance as baseline_balance, and if the same account exposes transaction or activity history store the current visible history state as baseline_history, then assert the funding action is available for that account.

## Step 3 ⏭ skipped

## Step 4 ⏭ skipped
