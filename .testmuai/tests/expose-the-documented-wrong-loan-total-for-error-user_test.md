---
assurance:
  id: t-22
  base: sha256:cfad0f8166a4a9d04d1ba1a1664e48b48b5bc34e5f11b98125bbd6fb78743751
---
# Expose the documented wrong loan total for error_user without generic failure messaging

> Prove that error_user reaches a dashboard/admin/navigation path with loan information, shows the documented wrong-loan-total condition, and keeps that state distinguishable from generic failure.

## Step 1

On https://qaplayground.com/bank/login, ensure the Bank Demo is at the login page and capture baseline: successful active-user login submitted from the Bank Demo login page.

## Step 2 @verifies ac-56

On the Bank Demo login page, sign in with username error_user and password bank_sauce, then assert the resulting banking experience loads as the authenticated experience appropriate to that persona.

## Step 3 @verifies ac-53, ac-54

From the authenticated error_user banking experience, navigate through the visible banking navigation to the first loan-related view the product exposes, then assert the view shows a loan total that conflicts with supporting loan data in the same view and that the screen is not presented as a generic application or network failure.
