---
assurance:
  id: t-10
  base: sha256:f9c91d899cdf21b908226de35860c795f981653f9963fd8659b09793ffeb5c3f
---
# Authenticate as admin_user into the administrative banking experience

> Prove that admin_user authentication lands in the intended administrative experience and exposes admin-distinct information or controls plus authorized administrative capabilities or data.

## Step 1

Open https://qaplayground.com/bank/login in a fresh browser session and store the visible unauthenticated login page state as baseline_login_state.

## Step 2 @verifies ac-25

On the QA Playground Bank Demo login page at https://qaplayground.com/bank/login, sign in with username admin_user and password admin_sauce, then assert the session leaves the unauthenticated login state and reaches the administrative experience for admin_user.

## Step 3 @verifies ac-26, ac-27

From the authenticated admin_user landing/dashboard and its visible banking navigation, inspect the role-specific content exposed to the session, then assert at least one administrative capability or administrative data point is visible and the information or controls are distinguishable from ordinary customer-facing banking information.
