---
test: ../reject-a-non-numeric-transfer-amount-without-creating_test.md
status: failed
started: 2026-09-11T20:42:38.873Z
duration_s: 104
session_id: 00c19497-3b88-4d11-add2-e9cd4603e728
---

# Reject a non-numeric transfer amount without creating partial transfer state — Result

## Step 1 ✓ passed (27.6s)
md5: c4dc508a6d5cc977e92f885d537c6d6f
Open https://qaplayground.com/bank/login in the browser and sign in as standard_user with password bank_sauce until the authenticated banking experience is visible.

## Step 2 ✓ passed (28.6s)
md5: 806e9500aa4e01aae3f9e0576e20a240
In the authenticated banking experience for standard_user, open the transfer or money-movement form and locate the source account selector, destination account selector, and monetary amount input, then assert all three transfer inputs are present.

## Step 3 ✗ failed (43.5s)
md5: ad727fa8053ff6756a436ed906852261
Reason: AP determined agent is stuck — no viable actions remain — bug verdict: Agent stalled on the transfer form before capturing account baselines [automation_bug/agent_misstep, confidence 0.98]
In the accounts and transaction/activity areas for the accounts named savings1000 and checkings500, store the current displayed source balance, destination balance, and relevant visible history snapshot as non_numeric_transfer_baseline.

## Step 4 ⏭ skipped
