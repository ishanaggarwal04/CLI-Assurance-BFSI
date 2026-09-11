---
assurance:
  id: t-19
  base: sha256:c7cd16218c2c09f07c9c4d8203446c132415a4876ee008161c3b9b602f718e81
---
# Keep administrative-only capabilities out of the standard_user dashboard

> Prove that a standard_user banking experience does not surface administrative-only capabilities or data.

## Step 1

On https://qaplayground.com/bank/login, ensure the Bank Demo is at the login page and capture baseline: successful active-user login submitted from the Bank Demo login page.

## Step 2 @verifies ac-56, ac-57

On the Bank Demo login page, sign in with username standard_user and password bank_sauce, then assert the resulting banking experience loads as the authenticated standard-user dashboard for that persona.

## Step 3 @verifies ac-50

Across the visible standard_user dashboard and its banking navigation, inspect the available data and actions, then assert no administrative-only capabilities or administrative-only data are exposed in this banking experience.
