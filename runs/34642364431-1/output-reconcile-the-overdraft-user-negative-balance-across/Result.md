---
test: ../reconcile-the-overdraft-user-negative-balance-across_test.md
status: passed
started: 2026-09-11T20:11:16.329Z
duration_s: 218
session_id: 72daa88f-ba76-4dea-a55a-ca48a873397d
---

# Reconcile the overdraft_user negative balance across dashboard-linked views — Result

## Step 1 ✓ passed (43.5s)
md5: 09fdfe674857cef9b8481da610e1621f
On https://qaplayground.com/bank/login, ensure the Bank Demo is at the login page and capture baseline: successful active-user login submitted from the Bank Demo login page.

## Step 2 ✓ passed (62.3s)
md5: 89a4472ce789edb5657432b75a88553a
On the Bank Demo login page, sign in with username overdraft_user and password bank_sauce, then assert the resulting banking experience loads as the authenticated overdraft-user view and visibly shows a negative balance.

## Step 3 ✓ passed (39.5s)
md5: 5641bc88d81b8dd93bc0172c8df1bffa
On the overdraft_user dashboard, inspect the overview content and available banking navigation, then assert relevant accounts and balances are represented directly on the dashboard or are reachable from that navigation.

## Step 4 ✓ passed (33.2s)
md5: f7b505a3cb1beb5b995c82209d9c31a2
From the dashboard, open the transaction or activity area associated with the negative-balance account, then assert relevant transaction or activity information is represented or accessible for that overdraft state.

## Step 5 ✓ passed (35.6s)
md5: ee7aa73af578de850e63a4ce10cd7b23
Compare the negative-balance account shown on the overdraft_user dashboard with the corresponding account and transaction details reached from that overview, then assert every displayed account or transaction value for that record remains consistent across the linked views.
