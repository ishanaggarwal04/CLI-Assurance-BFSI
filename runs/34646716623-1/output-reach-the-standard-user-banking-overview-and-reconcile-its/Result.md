---
test: ../reach-the-standard-user-banking-overview-and-reconcile-its_test.md
status: passed
started: 2026-09-11T20:59:05.487Z
duration_s: 254
session_id: 1d2755c3-72cd-4f6a-b092-a246b8abccbe
---

# Reach the standard_user banking overview and reconcile its linked account state — Result

## Step 1 ✓ passed (40.4s)
md5: 09fdfe674857cef9b8481da610e1621f
On https://qaplayground.com/bank/login, ensure the Bank Demo is at the login page and capture baseline: successful active-user login submitted from the Bank Demo login page.

## Step 2 ✓ passed (28.8s)
md5: 370e4c8e2157e2e33c0b5cd49a25bfe4
On the Bank Demo login page, sign in with username standard_user and password bank_sauce, then assert the resulting banking experience loads as the authenticated standard-user overview for that persona.

## Step 3 ✓ passed (66.7s)
md5: af099dca3a8b42c8e91c1a881481e83f
On the standard_user dashboard, inspect the overview cards and banking navigation, then assert relevant accounts and balances are represented directly on the dashboard or are reachable from the banking navigation.

## Step 4 ✓ passed (32.5s)
md5: e70bdbacb01fe791d50e3c8734570660
From the standard_user dashboard, open the transaction or activity area exposed by the banking navigation, then assert relevant transaction or activity information is represented or accessible where the product supports it.

## Step 5 ✓ passed (82.2s)
md5: 01387cf7a8912d6c8d66c2c7dcd0ed1e
From a dashboard-listed account or balance, open the corresponding detailed banking view for the same record, then assert every displayed account or transaction value shown on the dashboard stays consistent with the corresponding values shown elsewhere in the application.
