---
assurance:
  id: t-24
  base: sha256:c7dd2ee61a484a217e39c18391ba3821c46d020d795d6aab3d220308d22bb93e
---
# Show loading progress and resolve to a consistent dashboard for slow_user

> Prove that slow_user sees understandable loading or progress feedback and eventually reaches a consistent authenticated banking experience.

## Step 1

On https://qaplayground.com/bank/login, ensure the Bank Demo is at the login page and capture baseline: successful active-user login submitted from the Bank Demo login page.

## Step 2 @verifies ac-60

On the Bank Demo login page, sign in with username slow_user and password bank_sauce, and when the banking experience enters its intermediate loading state capture baseline: slow_user banking experience is in a loading state, then assert a user-understandable loading or progress indication is shown while the overview is still resolving.

## Step 3 @verifies ac-56, ac-57, ac-61

Allow the slow_user banking experience to finish resolving without re-submitting the login, then assert it resolves to the authenticated experience appropriate to slow_user with persona/state still matching that user and with internally consistent banking state.
