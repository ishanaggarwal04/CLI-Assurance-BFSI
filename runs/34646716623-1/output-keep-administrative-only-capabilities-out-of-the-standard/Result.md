---
test: ../keep-administrative-only-capabilities-out-of-the-standard_test.md
status: passed
started: 2026-09-11T20:58:47.589Z
duration_s: 180
session_id: 2fe3fa21-f85b-4829-aae9-ffa1fd1c5365
---

# Keep administrative-only capabilities out of the standard_user dashboard — Result

## Step 1 ✓ passed (44s)
md5: 09fdfe674857cef9b8481da610e1621f
On https://qaplayground.com/bank/login, ensure the Bank Demo is at the login page and capture baseline: successful active-user login submitted from the Bank Demo login page.

## Step 2 ✓ passed (48.3s)
md5: a53478a6864bf2c7974655c978468766
On the Bank Demo login page, sign in with username standard_user and password bank_sauce, then assert the resulting banking experience loads as the authenticated standard-user dashboard for that persona.

## Step 3 ✓ passed (83.9s)
md5: a5ad4d7fee179cb1159f935c3fcaee7b
Across the visible standard_user dashboard and its banking navigation, inspect the available data and actions, then assert no administrative-only capabilities or administrative-only data are exposed in this banking experience.
