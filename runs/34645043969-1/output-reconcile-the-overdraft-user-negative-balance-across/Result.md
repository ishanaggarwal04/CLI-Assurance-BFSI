---
test: ../reconcile-the-overdraft-user-negative-balance-across_test.md
status: failed
started: 2026-09-11T20:40:57.277Z
duration_s: 106
session_id: 03ccac2c-1059-4729-b91c-a4d65b649323
---

# Reconcile the overdraft_user negative balance across dashboard-linked views — Result

## Step 1 ✓ passed (32.7s)
md5: 09fdfe674857cef9b8481da610e1621f
On https://qaplayground.com/bank/login, ensure the Bank Demo is at the login page and capture baseline: successful active-user login submitted from the Bank Demo login page.

## Step 2 ✗ failed (69.2s)
md5: 89a4472ce789edb5657432b75a88553a
Reason: Final verification failed: "the resulting banking experience loads as the authenticated overdraft-user view and visibly shows a negative balance" — bug verdict: Agent asserted a negative balance without opening account details [automation_bug/agent_misstep, confidence 0.97]
On the Bank Demo login page, sign in with username overdraft_user and password bank_sauce, then assert the resulting banking experience loads as the authenticated overdraft-user view and visibly shows a negative balance.

## Step 3 ⏭ skipped

## Step 4 ⏭ skipped

## Step 5 ⏭ skipped
