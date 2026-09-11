---
test: ../keep-administrative-only-capabilities-out-of-the-standard_test.md
status: passed
started: 2026-09-11T20:09:37.145Z
duration_s: 195
session_id: e48d5fbf-7b4c-4521-9ab9-57309de6530c
---

# Keep administrative-only capabilities out of the standard_user dashboard — Result

## Step 1 ✓ passed (59.3s)
md5: 09fdfe674857cef9b8481da610e1621f
On https://qaplayground.com/bank/login, ensure the Bank Demo is at the login page and capture baseline: successful active-user login submitted from the Bank Demo login page.

## Step 2 ✓ passed (42.1s)
md5: a53478a6864bf2c7974655c978468766
On the Bank Demo login page, sign in with username standard_user and password bank_sauce, then assert the resulting banking experience loads as the authenticated standard-user dashboard for that persona.

## Step 3 ✓ passed (90.4s)
md5: a5ad4d7fee179cb1159f935c3fcaee7b
Across the visible standard_user dashboard and its banking navigation, inspect the available data and actions, then assert no administrative-only capabilities or administrative-only data are exposed in this banking experience.
