---
assurance:
  id: t-21
  base: sha256:dcb838c91e45a3c20e8613fc337f3793623fe775442dd378b7940cb37c0c7980
---
# Reconcile the overdraft_user negative balance across dashboard-linked views

> Prove that overdraft_user sees a negative balance and that the balance reconciles with the related account and transaction information.

## Step 1

On https://qaplayground.com/bank/login, ensure the Bank Demo is at the login page and capture baseline: successful active-user login submitted from the Bank Demo login page.

## Step 2 @verifies ac-56, ac-57, ac-55

On the Bank Demo login page, sign in with username overdraft_user and password bank_sauce, then assert the resulting banking experience loads as the authenticated overdraft-user view and visibly shows a negative balance.

## Step 3 @verifies ac-58

On the overdraft_user dashboard, inspect the overview content and available banking navigation, then assert relevant accounts and balances are represented directly on the dashboard or are reachable from that navigation.

## Step 4 @verifies ac-59

From the dashboard, open the transaction or activity area associated with the negative-balance account, then assert relevant transaction or activity information is represented or accessible for that overdraft state.

## Step 5 @verifies ac-49

Compare the negative-balance account shown on the overdraft_user dashboard with the corresponding account and transaction details reached from that overview, then assert every displayed account or transaction value for that record remains consistent across the linked views.
