---
test: ../block-transfer-access-within-the-frozen-user-banking_test.md
status: passed
started: 2026-09-11T20:36:57.131Z
duration_s: 137
session_id: ba6f82c4-e302-4d59-85cc-d5d554868f62
---

# Block transfer access within the frozen_user banking experience — Result

## Step 1 ✓ passed (43.6s)
md5: 09fdfe674857cef9b8481da610e1621f
On https://qaplayground.com/bank/login, ensure the Bank Demo is at the login page and capture baseline: successful active-user login submitted from the Bank Demo login page.

## Step 2 ✓ passed (45.3s)
md5: a78f77967509588b53a675dfc8bb13c0
On the Bank Demo login page, sign in with username frozen_user and password bank_sauce, then assert the resulting banking experience loads as an authenticated frozen-user experience rather than leaving the user in a generic failure state.

## Step 3 ✓ passed (40.8s)
md5: 74a3dc5d91c45d31a6ce74c5e52cfd98
From the authenticated frozen_user banking experience, open any visible transfer entry point or transfer-related action that the banking navigation exposes, then assert transfer use is unavailable, disabled, or clearly rejected and no normal UI path allows the transfer to complete.
