---
assurance:
  id: t-18
  base: sha256:c3afec519fc97bdfef29534170bdb9a840d961dca97ce4cd060e4aa83a8e4f73
---
# Block transfer access within the frozen_user banking experience

> Prove that frozen_user reaches any permitted authenticated banking overview state while transfer functionality is unavailable, disabled, or rejected through normal UI paths.

## Step 1

On https://qaplayground.com/bank/login, ensure the Bank Demo is at the login page and capture baseline: successful active-user login submitted from the Bank Demo login page.

## Step 2 @verifies ac-56, ac-57

On the Bank Demo login page, sign in with username frozen_user and password bank_sauce, then assert the resulting banking experience loads as an authenticated frozen-user experience rather than leaving the user in a generic failure state.

## Step 3 @verifies ac-52

From the authenticated frozen_user banking experience, open any visible transfer entry point or transfer-related action that the banking navigation exposes, then assert transfer use is unavailable, disabled, or clearly rejected and no normal UI path allows the transfer to complete.
