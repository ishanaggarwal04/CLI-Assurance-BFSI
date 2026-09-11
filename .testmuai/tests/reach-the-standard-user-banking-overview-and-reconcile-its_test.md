---
assurance:
  id: t-23
  base: sha256:be26477a2c31901f732107c18f01f2b6aa0150301bde215ba7ceb183f99d935c
---
# Reach the standard_user banking overview and reconcile its linked account state

> Prove that a successful standard_user login lands on the authenticated banking overview and exposes or links to the relevant banking state for that persona.

## Step 1

On https://qaplayground.com/bank/login, ensure the Bank Demo is at the login page and capture baseline: successful active-user login submitted from the Bank Demo login page.

## Step 2 @verifies ac-56, ac-57

On the Bank Demo login page, sign in with username standard_user and password bank_sauce, then assert the resulting banking experience loads as the authenticated standard-user overview for that persona.

## Step 3 @verifies ac-58

On the standard_user dashboard, inspect the overview cards and banking navigation, then assert relevant accounts and balances are represented directly on the dashboard or are reachable from the banking navigation.

## Step 4 @verifies ac-59

From the standard_user dashboard, open the transaction or activity area exposed by the banking navigation, then assert relevant transaction or activity information is represented or accessible where the product supports it.

## Step 5 @verifies ac-49

From a dashboard-listed account or balance, open the corresponding detailed banking view for the same record, then assert every displayed account or transaction value shown on the dashboard stays consistent with the corresponding values shown elsewhere in the application.
