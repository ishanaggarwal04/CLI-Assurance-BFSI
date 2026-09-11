---
test: ../expose-the-documented-wrong-loan-total-for-error-user_test.md
status: passed
started: 2026-09-11T20:39:33.632Z
duration_s: 167
session_id: 400c8ea8-e7ce-48dc-8718-09ee1f94db57
---

# Expose the documented wrong loan total for error_user without generic failure messaging — Result

## Step 1 ✓ passed (59.9s)
md5: 09fdfe674857cef9b8481da610e1621f
On https://qaplayground.com/bank/login, ensure the Bank Demo is at the login page and capture baseline: successful active-user login submitted from the Bank Demo login page.

## Step 2 ✓ passed (42.6s)
md5: 07dfa4bae9a4cb215e34f7fc22040581
On the Bank Demo login page, sign in with username error_user and password bank_sauce, then assert the resulting banking experience loads as the authenticated experience appropriate to that persona.

## Step 3 ✓ passed (59.9s)
md5: f8ab2b6fa10716143b9e18e7d997273e
From the authenticated error_user banking experience, navigate through the visible banking navigation to the first loan-related view the product exposes, then assert the view shows a loan total that conflicts with supporting loan data in the same view and that the screen is not presented as a generic application or network failure.
