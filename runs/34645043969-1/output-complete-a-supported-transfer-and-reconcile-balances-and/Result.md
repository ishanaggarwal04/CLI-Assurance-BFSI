---
test: ../complete-a-supported-transfer-and-reconcile-balances-and_test.md
status: failed
started: 2026-09-11T20:38:10.936Z
duration_s: 317
session_id: 06729134-96a6-49e4-bb1e-3e9ea670f05d
---

# Complete a supported transfer and reconcile balances and history for standard_user — Result

## Step 1 ✓ passed (25s)
md5: c4dc508a6d5cc977e92f885d537c6d6f
Open https://qaplayground.com/bank/login in the browser and sign in as standard_user with password bank_sauce until the authenticated banking experience is visible.

## Step 2 ✓ passed (31.8s)
md5: 806e9500aa4e01aae3f9e0576e20a240
In the authenticated banking experience for standard_user, open the transfer or money-movement form and locate the source account selector, destination account selector, and monetary amount input, then assert all three transfer inputs are present.

## Step 3 ✓ passed (84.9s)
md5: ca1be78aa2ff1c33891d34022fdf0ea7
In the accounts and transaction/activity areas for the accounts named savings1000 and checkings500, store the current displayed source balance, destination balance, and relevant visible history snapshot as successful_transfer_baseline.

## Step 4 ✗ failed (171.5s)
md5: 56b731d8116a671951dd3890f392156e
Reason: AP determined agent is stuck — no viable actions remain — bug verdict: Destination balance remains unchanged after successful transfer [application_issue/ui_data_defect, confidence 0.94]
Using the transfer form, move 200 from the account named savings1000 to the account named checkings500 and submit the transfer, then assert clear user-visible success feedback is shown and the displayed source and destination balances update consistently with that committed transfer.

## Step 5 ⏭ skipped
