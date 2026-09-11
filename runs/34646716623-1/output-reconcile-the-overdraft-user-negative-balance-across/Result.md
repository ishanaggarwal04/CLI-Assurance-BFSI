---
test: ../reconcile-the-overdraft-user-negative-balance-across_test.md
status: failed
started: 2026-09-11T20:59:40.010Z
duration_s: 154
session_id: 598b1cb3-1c8a-4c7c-b7ab-791632e9a9d5
---

# Reconcile the overdraft_user negative balance across dashboard-linked views — Result

## Step 1 ✓ passed (45.8s)
md5: 09fdfe674857cef9b8481da610e1621f
On https://qaplayground.com/bank/login, ensure the Bank Demo is at the login page and capture baseline: successful active-user login submitted from the Bank Demo login page.

## Step 2 ✗ failed (105s)
md5: 89a4472ce789edb5657432b75a88553a
Reason: Final verification failed: "the resulting banking experience loads as the authenticated overdraft-user view and visibly shows a negative balance" — bug verdict: Overdraft balance asserted before opening the account view [automation_bug/state_transition_bug, confidence 0.90]
On the Bank Demo login page, sign in with username overdraft_user and password bank_sauce, then assert the resulting banking experience loads as the authenticated overdraft-user view and visibly shows a negative balance.

## Step 3 ⏭ skipped

## Step 4 ⏭ skipped

## Step 5 ⏭ skipped
