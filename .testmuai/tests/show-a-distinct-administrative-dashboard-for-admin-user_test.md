---
assurance:
  id: t-20
  base: sha256:ab9caeb2541544e9cc8703a1159422c259a3dac10345821f6d48029cdc1389bc
---
# Show a distinct administrative dashboard for admin_user

> Prove that admin_user lands in the intended administrative experience and that it is distinguishable from the ordinary customer-facing dashboard.

## Step 1

On https://qaplayground.com/bank/login, ensure the Bank Demo is at the login page and capture baseline: successful active-user login submitted from the Bank Demo login page.

## Step 2 @verifies ac-56

On the Bank Demo login page, sign in with username admin_user and password admin_sauce, then assert the resulting banking experience loads as the authenticated experience appropriate to the administrative persona.

## Step 3 @verifies ac-51

Within the admin_user landing experience, inspect the visible information and controls that define the banking view, then assert at least one administrative information area or control is distinguishable from ordinary customer-facing banking information.
