---
assurance:
  id: t-9
  base: sha256:4e5fb484efa85018828df092726e76aee8dc38178e4395175b13021679e175ab
---
# Authenticate as standard_user without inheriting administrative-only access

> Prove that a standard user can authenticate into the normal full-access banking experience without receiving administrative-only view, data, or capabilities.

## Step 1

Open https://qaplayground.com/bank/login in a fresh browser session and store the visible unauthenticated login page state as baseline_login_state.

## Step 2 @verifies ac-28

On the QA Playground Bank Demo login page at https://qaplayground.com/bank/login, sign in with username standard_user and password bank_sauce, then assert the session leaves the unauthenticated login state and shows the normal/full-access banking experience represented by standard_user.

## Step 3 @verifies ac-24

From the authenticated standard_user landing/dashboard and its visible banking navigation, inspect the role-specific content available in the session, then assert no administrative view, administrative data, or administrative-only capability is exposed.
