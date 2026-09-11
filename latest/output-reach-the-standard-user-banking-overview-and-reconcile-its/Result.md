---
test: ../reach-the-standard-user-banking-overview-and-reconcile-its_test.md
status: failed
started: 2026-09-11T20:11:06.815Z
duration_s: 279
session_id: 303d920f-8f05-4a07-96a5-ea7c598a3af3
---

# Reach the standard_user banking overview and reconcile its linked account state — Result

## Step 1 ✓ passed (59s)
md5: 09fdfe674857cef9b8481da610e1621f
On https://qaplayground.com/bank/login, ensure the Bank Demo is at the login page and capture baseline: successful active-user login submitted from the Bank Demo login page.

## Step 2 ✓ passed (44.5s)
md5: 370e4c8e2157e2e33c0b5cd49a25bfe4
On the Bank Demo login page, sign in with username standard_user and password bank_sauce, then assert the resulting banking experience loads as the authenticated standard-user overview for that persona.

## Step 3 ✓ passed (35.2s)
md5: af099dca3a8b42c8e91c1a881481e83f
On the standard_user dashboard, inspect the overview cards and banking navigation, then assert relevant accounts and balances are represented directly on the dashboard or are reachable from the banking navigation.

## Step 4 ✓ passed (29.5s)
md5: e70bdbacb01fe791d50e3c8734570660
From the standard_user dashboard, open the transaction or activity area exposed by the banking navigation, then assert relevant transaction or activity information is represented or accessible where the product supports it.

## Step 5 ✗ failed (107.9s)
md5: 01387cf7a8912d6c8d66c2c7dcd0ed1e
Reason: Final verification failed: "every displayed account or transaction value shown on the dashboard {{dashboard_account_or_transaction_values}} stays consistent with the corresponding values shown elsewhere in the application {{detailed_account_or_transaction_values}}" — bug verdict: Assertion compares mixed-account transaction values with one account view [automation_bug/agent_misstep, confidence 0.91]
From a dashboard-listed account or balance, open the corresponding detailed banking view for the same record, then assert every displayed account or transaction value shown on the dashboard stays consistent with the corresponding values shown elsewhere in the application.
