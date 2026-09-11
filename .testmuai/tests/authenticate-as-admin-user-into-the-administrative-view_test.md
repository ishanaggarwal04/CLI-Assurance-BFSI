---
assurance:
  id: t-4
  base: sha256:4c0d9f106df3e219c598744f17f4f7111d085dbc4b85036e718d7f5107bb3e19
---
# Authenticate as admin_user into the administrative view

> Prove the administrative credential establishes an authenticated session that exposes the intended administrative view rather than the standard-user experience.

## Step 1

Open https://qaplayground.com/bank/login in a browser and store the visible unauthenticated login page as baseline_login_state.

## Step 2 @verifies ac-15, ac-16

Enter username admin_user and password admin_sauce on the Bank Demo login page and submit Sign In, then assert the login surface is replaced by an authenticated administrative view with admin-specific information or controls that are distinguishable from the ordinary customer banking experience.
