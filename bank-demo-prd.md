# QA Playground — Bank Demo Application
## Product Requirements Document

| Document attribute | Specification |
|---|---|
| Product | QA Playground Bank Demo |
| Entry point | https://qaplayground.com/bank/login |
| Product category | Simulated digital banking / end-to-end practice application |
| Primary product areas | Authentication, dashboard, accounts, balances, transactions, role-specific states |
| Document intent | Describe the product as a standalone application: capabilities, data, rules, states, validations, roles, UI behavior and acceptance criteria. |
| Test data | All credentials visibly supplied by the Bank Demo login page are documented in this PRD. |

Scope principle: This document is a product PRD. It does not prescribe test cases, example journeys, automation scripts, locators or execution sequences. The requirements are intentionally expressed as product capabilities and expected behavior so that different users and systems can derive their own scenarios.

QA Playground publicly describes the Bank Demo as a full simulated banking application covering login, accounts, dashboard and transaction management, and its Demo Apps page describes the Bank Demo as supporting forms, validations and account workflows.

## 1. Product Overview

The QA Playground Bank Demo is a browser-based simulated banking product intended to model core digital-banking interactions in a controlled environment. The product provides an authentication boundary, a banking dashboard, account-oriented functionality and transaction management. QA Playground positions the Bank Demo as a realistic multi-page banking workflow suitable for end-to-end practice.

The application should be understood as a stateful product. Authentication determines access. User/account state determines what balances and transactions are visible. Financial operations alter application state, and subsequent views must reflect those committed changes consistently.

### 1.1 Product Objectives

- Provide a realistic but simulated banking environment.
- Represent multiple user personas with different account/application states.
- Allow authenticated users to interact with banking entities and financial state.
- Make account balances and transaction state observable through the user interface.
- Provide validation and failure states that resemble real application behavior.
- Provide distinct standard and administrative experiences where supported by the assigned user role.
- Make the product deterministic enough for repeated functional evaluation while preserving meaningful stateful behavior.

### 1.2 Product Boundaries

- The product is a simulated banking environment and must not be interpreted as a real banking institution.
- The credentials listed in this document are demo credentials intentionally exposed by the product.
- No real monetary value is associated with balances displayed by the application.
- The product specification covers behavior visible through the application and does not require implementation-specific APIs or database access.

## 2. User Personas and Demo Credentials

The login page explicitly exposes a Test credentials table containing multiple predefined users. These are product-provided personas/test fixtures and are part of the application's documented behavior.

| Username | Password | Description / Persona State |
|---|---|---|
| standard_user | bank_sauce | Full access |
| locked_user | bank_sauce | Locked account |
| frozen_user | bank_sauce | Frozen — no transfers |
| overdraft_user | bank_sauce | Negative balance |
| slow_user | bank_sauce | Slow loading |
| error_user | bank_sauce | Wrong loan total |
| admin_user | admin_sauce | Admin view |

Credential source: These values are transcribed from the Test credentials section visibly presented on the Bank Demo login page. The page labels the columns Username, Password and Description. The credentials should therefore be treated as first-class product test data rather than as external assumptions.

### 2.1 Persona Requirements

| Persona | Product requirement |
|---|---|
| standard_user | Must represent the normal/full-access banking experience available to a standard user. |
| locked_user | Must represent an account in a locked state. The application must enforce the consequences of the locked state at authentication/access time. |
| frozen_user | Must represent a frozen banking state in which transfers are not permitted, as indicated by the credential description. |
| overdraft_user | Must represent a user/account state containing a negative balance. The negative balance must remain internally consistent with the account and transaction state displayed by the application. |
| slow_user | Must exercise the product's intentionally slow-loading behavior. Loading states should remain understandable and should eventually resolve according to the application's intended behavior. |
| error_user | Must represent the intentionally incorrect loan-total state described by the credential fixture. The application should expose the corresponding data/error condition consistently wherever that state is represented. |
| admin_user | Must represent the administrative view and expose the administrative capabilities/data intended by the product. |

The descriptions above document the explicit semantics shown on the login page. Where the live application exposes additional UI, permissions or state-specific behavior for a persona, that behavior is part of the product's role/state contract and should be consistent throughout the application.

## 3. Authentication

### 3.1 Login Page

| ID | Requirement | Expected product behavior |
|---|---|---|
| AUTH-01 | Login entry point | The application provides a dedicated login page at the Bank Demo login URL. |
| AUTH-02 | Username input | The login interface provides a username field with a clear input affordance. |
| AUTH-03 | Password input | The login interface provides a password field and treats entered password content as obscured input by default. |
| AUTH-04 | Password visibility | The visible eye control provides a way to reveal/hide the entered password without changing the credential. |
| AUTH-05 | Remember me | The login interface provides a Remember me checkbox representing an optional persistence/session preference. |
| AUTH-06 | Sign In | A clearly labeled Sign In control submits the authentication request. |
| AUTH-07 | Forgot password | A Forgot password entry point is available from the login page. |
| AUTH-08 | Credential fixtures | The page visibly provides all seven demo credential records documented in Section 2. |
| AUTH-09 | Valid authentication | A valid active credential establishes an authenticated session and exposes the appropriate post-login experience. |
| AUTH-10 | Invalid authentication | Invalid credentials do not grant access and produce an understandable failure state. |
| AUTH-11 | Locked authentication | A locked account must not be treated as a normal active session. |

### 3.2 Session Management

- An authenticated session must have a clear distinction from the unauthenticated login state.
- The application must preserve the appropriate user identity while the session is active.
- Logout must terminate the active authenticated session.
- After logout, protected banking content must not remain actionable as an authenticated experience.
- Session persistence behavior must respect the Remember me control when the feature is implemented.
- Expired or invalid sessions must be handled gracefully rather than leaving the user in a partially authenticated state.

## 4. Dashboard / Home Banking Experience

The dashboard is the authenticated banking overview. It should present the user's relevant banking state and provide access to the application's supported account and transaction capabilities. QA Playground explicitly describes the Bank Demo as including a dashboard.

| ID | Requirement | Expected product behavior |
|---|---|---|
| DASH-01 | Authenticated landing | A successful active-user login leads to the appropriate authenticated banking experience. |
| DASH-02 | User context | The dashboard reflects the authenticated user's persona and associated state. |
| DASH-03 | Account visibility | Relevant accounts and balances are represented in the dashboard or reachable through the banking navigation. |
| DASH-04 | Transaction visibility | Relevant transaction/activity information is represented or accessible where supported. |
| DASH-05 | State consistency | Dashboard values must remain consistent with the underlying account/transaction state shown elsewhere in the application. |
| DASH-06 | Role awareness | Administrative users receive the intended administrative view rather than being treated identically to a standard user. |
| DASH-07 | Exceptional states | Locked, frozen, overdraft, slow-loading and error-oriented personas must produce their intended state-specific experience. |

## 5. Account Management

Account management is a core product domain. The product should allow the authenticated user to interact with supported banking accounts and maintain accurate account-level state.

| ID | Requirement | Expected product behavior |
|---|---|---|
| ACCT-01 | Account listing | The user can view the accounts available to the current user. |
| ACCT-02 | Account identity | Each account is distinguishable by its displayed name/identifier and any supported account type information. |
| ACCT-03 | Account balance | Each account exposes a current balance consistent with committed financial operations. |
| ACCT-04 | Account creation | Where the live product provides account creation, an authenticated user can provide the required account information and create an account. |
| ACCT-05 | Account validation | Required account fields are validated before an invalid account can be committed. |
| ACCT-06 | Account persistence | A successfully created account remains available according to the application's persistence model. |
| ACCT-07 | Account state | Special states such as frozen or overdraft must be reflected accurately in account behavior and displayed state. |
| ACCT-08 | Account consistency | The same account must not display contradictory balances or identity information across product surfaces. |

### 5.1 Account Data Model

| Data element | Purpose |
|---|---|
| Account identifier/name | Human-readable identification of the banking account. |
| Account type | Classification of the account where supported by the product. |
| Current balance | Current monetary state of the account. |
| Account status | Active, frozen, locked or other state where exposed. |
| Associated user | User/persona to whom the account belongs. |
| Transaction history | Financial events associated with the account where supported. |

## 6. Transaction Management

Transaction management covers financial events that change or represent account state. The public product description explicitly identifies transaction management as a core Bank Demo capability.

| ID | Requirement | Expected product behavior |
|---|---|---|
| TXN-01 | Transaction visibility | Users can view supported transaction/activity information associated with their banking state. |
| TXN-02 | Transaction amount | A transaction displays the amount associated with the financial event. |
| TXN-03 | Transaction direction | Where relevant, the UI distinguishes money entering versus leaving an account. |
| TXN-04 | Transaction account | A transaction can be associated with the relevant account(s). |
| TXN-05 | Transaction state | Only committed financial changes should be represented as completed financial state. |
| TXN-06 | Balance relationship | Completed transactions must reconcile with the displayed account balances. |
| TXN-07 | History persistence | Committed transaction history should remain available according to the application's persistence model. |
| TXN-08 | Failure handling | Rejected operations must not create misleading completed transaction records. |

## 7. Money Movement / Transfers

Transfers are part of the banking product's state-changing behavior. The documented frozen-user credential explicitly states 'no transfers', establishing that transfer permission is persona/state dependent.

| ID | Requirement | Expected product behavior |
|---|---|---|
| TRF-01 | Transfer capability | The product provides a supported transfer mechanism where permitted for the current user/account state. |
| TRF-02 | Source selection | A transfer identifies the account from which funds are moved. |
| TRF-03 | Destination selection | A transfer identifies the account receiving funds. |
| TRF-04 | Amount | A transfer contains a monetary amount subject to product validation. |
| TRF-05 | Positive amount | Invalid monetary values must not be silently accepted as successful transfers. |
| TRF-06 | Sufficient funds | The product must apply its supported balance/overdraft rules when determining whether a transfer can complete. |
| TRF-07 | Frozen restriction | The frozen persona must not be permitted to perform transfers, consistent with its explicit fixture description. |
| TRF-08 | Atomicity | A failed transfer must not leave the source and destination in an inconsistent partially-updated state. |
| TRF-09 | Balance update | A completed transfer must produce consistent source and destination balance changes. |
| TRF-10 | Transaction record | A completed transfer must be represented in transaction/activity history where that feature is exposed. |

## 8. Deposits / Funding / Balance Changes

Where the live Bank Demo exposes deposit, add-funds or equivalent balance-increase functionality, it forms part of the account state-management domain.

| ID | Requirement | Expected product behavior |
|---|---|---|
| FUND-01 | Funding action | Supported users can initiate the product's supported balance-increase operation. |
| FUND-02 | Amount validation | The monetary input must obey the application's accepted numeric and business rules. |
| FUND-03 | Balance update | A successful funding operation increases the appropriate balance by the committed amount. |
| FUND-04 | Transaction linkage | A successful funding operation is reflected in transaction history where supported. |
| FUND-05 | Failure integrity | A failed funding operation must not create a false balance or completed transaction. |

## 9. Overdraft State

The overdraft_user fixture explicitly represents a negative-balance condition. This makes overdraft handling an intentional product state rather than an accidental edge case.

- The application must be capable of displaying a negative balance for the overdraft persona.
- The negative balance must be displayed consistently wherever the account balance appears.
- Transaction/activity information must reconcile with the negative balance.
- Any transfer/funding rules involving an overdraft state must follow the application's defined business rules rather than assuming that all negative balances are invalid.
- The overdraft state must not be visually or semantically confused with an application error.

## 10. Special Persona States

### 10.1 Locked User

- The locked_user fixture represents an explicitly locked account.
- Authentication must respect the locked state.
- The application must provide a clear user-visible outcome when a locked account attempts to authenticate.
- A locked state must not accidentally grant the same access as standard_user.

### 10.2 Frozen User

- The frozen_user fixture represents a frozen account with the explicit restriction 'no transfers'.
- The user may still be able to authenticate/view permitted information depending on the product's implementation.
- Transfer functionality must be unavailable, disabled or rejected for this persona.
- The restriction must not be bypassable through normal UI interaction.

### 10.3 Slow User

- The slow_user fixture represents intentionally slow-loading behavior.
- The application should communicate loading/progress rather than appearing permanently broken.
- Once loading completes, the resulting state should be internally consistent.
- Slow behavior should not cause duplicate submissions or contradictory state when the user waits for completion.

### 10.4 Error User

- The error_user fixture is explicitly described as 'Wrong loan total'.
- The product must expose the intended incorrect-loan-total condition in the relevant administrative/dashboard/loan-related representation if present.
- The error state should remain distinguishable from network failure or generic application failure.
- Other unrelated banking values should not become corrupted merely because this persona contains the intentional loan-total discrepancy.

### 10.5 Admin User

- The admin_user fixture represents the administrative view.
- Administrative authentication must lead to the intended administrative experience.
- Administrative information and controls should be distinguishable from ordinary customer-facing banking information.
- Administrative capabilities must be restricted to the administrative persona where the product defines role-based access.
- A standard user must not automatically inherit administrative-only capabilities.

## 11. Loan / Loan-Total Representation

The existence of the error_user fixture with the description 'Wrong loan total' establishes that the product includes, or is intended to include, a loan-related total or representation in at least one banking view.

| ID | Requirement | Expected product behavior |
|---|---|---|
| LOAN-01 | Loan information | Where the product exposes loan information, it should identify the relevant loan/account context. |
| LOAN-02 | Loan total | The product should display a loan total according to the current user's state. |
| LOAN-03 | Error fixture | error_user must expose the intentionally incorrect loan-total state described by its credential fixture. |
| LOAN-04 | Consistency | Loan totals should be internally consistent with any supporting loan data displayed in the same view. |
| LOAN-05 | Error isolation | An intentional loan-total discrepancy must not incorrectly alter unrelated account balances or transactions. |

## 12. Validation and Error Handling

The Bank Demo is explicitly positioned as a practice application involving forms and validations.

| Domain | Validation expectation |
|---|---|
| Username | Required for authentication; malformed or unknown values must not authenticate. |
| Password | Required for authentication; incorrect values must not authenticate. |
| Account fields | Required account information must be validated before creation/commit. |
| Monetary inputs | Must accept only values supported by the application's business rules and formatting rules. |
| Transfer source/destination | Must identify valid eligible accounts. |
| Transfer amount | Must comply with numeric, positivity and available-funds/business-rule constraints. |
| Permission restrictions | Actions unavailable to a persona must be blocked or clearly rejected. |
| Network/loading failures | The user should receive an understandable state instead of silent data loss. |
| State conflicts | The product must avoid partial updates when a state-changing operation fails. |

## 13. Data Integrity and Consistency

- An account's displayed balance must represent its committed financial state.
- Transaction records and balances must agree after successful financial operations.
- A rejected transaction must not appear as completed financial activity.
- A user must not see another user's private account information through normal navigation.
- Role-specific data must remain consistent with the authenticated persona.
- The same account must retain a stable identity across dashboard, account and transaction views.
- State-changing operations should be idempotent from the user's perspective with respect to duplicate submissions where the product can detect them.
- Refreshing or navigating between supported banking views should not arbitrarily revert committed data.

## 14. Authorization and Access Control

| Area | Requirement |
|---|---|
| Unauthenticated state | Protected banking information and operations must not be available as an authenticated experience. |
| Standard user | Receives the normal/full-access experience represented by standard_user. |
| Locked user | Receives the restricted behavior associated with a locked account. |
| Frozen user | Cannot perform transfers, consistent with the fixture description. |
| Admin user | Receives the administrative view and associated authorized capabilities. |
| Cross-user isolation | A user should not be able to access another user's account information merely by manipulating normal UI navigation. |
| Session identity | All user-specific dashboard/account/transaction data must correspond to the currently authenticated identity. |

## 15. User Interface and Experience Requirements

| Area | Requirement |
|---|---|
| Login | Username/password fields, password visibility control, Remember me, Sign In and Forgot password are clearly presented. |
| Credential reference | The Test credentials section clearly presents username, password and description for all predefined personas. |
| Navigation | Authenticated users can discover the product's supported banking areas through visible navigation. |
| Feedback | Successful and failed state-changing operations have clear user-visible feedback. |
| Loading | Slow or asynchronous operations communicate that work is in progress. |
| Errors | Errors are understandable, associated with the relevant operation and do not silently discard user input when recovery is possible. |
| Balances | Monetary values are displayed consistently and unambiguously. |
| Tables/lists | Account and transaction collections should clearly associate each row/item with its relevant data. |
| Responsive behavior | Core banking controls remain usable at supported viewport sizes. |

## 16. Accessibility Requirements

- Form fields should have accessible labels or equivalent accessible names.
- The password visibility control should expose an understandable accessible name.
- Checkboxes and actionable controls should be keyboard operable.
- Validation and error messages should be discoverable by assistive technologies where practical.
- Color should not be the only mechanism for communicating success, failure, restriction or state.
- Loading states should be communicated in a way that does not leave assistive-technology users without feedback.

## 17. Security Requirements for the Simulated Product

Although the Bank Demo uses intentionally public demo credentials, it should still model sensible banking-product security boundaries.

- Passwords must be handled as password input and not displayed in plaintext by default.
- Protected banking views should require an appropriate authenticated session.
- Logout must invalidate the active authenticated experience.
- Authorization should be enforced consistently across user personas.
- A frozen/locked restriction must not be bypassable through ordinary UI actions.
- Administrative views must not be exposed to ordinary users.
- User-specific financial information must remain scoped to the authenticated identity.
- Error messages should avoid exposing unnecessary implementation details.

## 18. Non-Functional Requirements

| Category | Requirement |
|---|---|
| Reliability | Committed account and transaction state should remain consistent across supported navigation and refresh behavior. |
| Performance | Normal product interactions should respond within reasonable expectations; slow_user intentionally represents a delayed-loading state. |
| Usability | Core banking actions should be understandable without requiring knowledge of implementation details. |
| Consistency | The same business state should render consistently across relevant pages/components. |
| Maintainability | Product behavior should remain structured around clear entities: users, accounts, balances, transactions and roles. |
| Accessibility | Core authentication and banking interactions should support accessible interaction patterns. |
| Observability | Important success/failure states should be visible in the UI rather than silently changing state. |
| Data integrity | Financial state must not be partially updated by failed operations. |

## 19. Product State Model

| State | Meaning | Product expectation |
|---|---|---|
| Unauthenticated | No active user session | Only public/login functionality is available. |
| Authenticated | Valid user session | User-specific banking information and permitted operations are available. |
| Locked | Account is locked | Normal active-user access is restricted. |
| Frozen | Account is frozen | Transfer capability is prohibited. |
| Overdraft | Account has negative balance | Negative balance is represented as a valid special account state. |
| Loading | Application is retrieving/processing data | Progress is communicated and final state resolves consistently. |
| Error | Intentionally incorrect or failed application state | Error condition is visible without corrupting unrelated data. |
| Administrative | Admin persona/session | Administrative view and authorized data are exposed. |
| Logged out | Session terminated | Protected banking state is no longer actionable as authenticated content. |

## 20. Product Requirements Inventory

| Domain | Coverage |
|---|---|
| Authentication | Login page, credentials, password visibility, Remember me, Sign In, Forgot password, successful/failed authentication, locked state, session lifecycle. |
| User personas | Seven predefined credential fixtures and their explicit state descriptions. |
| Dashboard | Authenticated overview, user context, accounts, balances, transaction/activity representation and role-aware presentation. |
| Accounts | Account listing, identity, type, balance, creation where supported, validation, persistence and state. |
| Funding | Supported balance-increase operations, amount validation, balance update and transaction linkage. |
| Transfers | Source/destination, amount, permission, funds rules, frozen restriction, atomicity, balance updates and transaction records. |
| Transactions | History, amount, direction, account association, completion state and reconciliation. |
| Overdraft | Negative balance representation and consistency. |
| Loans | Loan-related total representation and intentional error fixture. |
| Administration | Admin view and role-specific access. |
| Validation | Required fields, invalid values, business rules, permissions and state errors. |
| Security | Session boundary, authorization, user isolation, password handling and protected views. |
| UX/accessibility | Labels, controls, feedback, loading, responsive behavior and accessible interaction. |

## 21. Product-Level Acceptance Criteria

| ID | Acceptance criterion |
|---|---|
| PRD-AC-01 | The Bank Demo is reachable at the documented login URL. |
| PRD-AC-02 | The login page visibly lists all seven predefined credential records and their descriptions. |
| PRD-AC-03 | Each credential fixture produces the product state represented by its description. |
| PRD-AC-04 | A valid full-access user can access the intended authenticated banking experience. |
| PRD-AC-05 | Locked users do not receive unrestricted normal access. |
| PRD-AC-06 | Frozen users cannot perform transfers. |
| PRD-AC-07 | Overdraft users can be represented with a negative balance without the application treating the balance itself as a rendering failure. |
| PRD-AC-08 | Slow-loading behavior provides a distinguishable loading state and eventually resolves as intended. |
| PRD-AC-09 | The error-user fixture exposes the documented wrong-loan-total condition. |
| PRD-AC-10 | The administrative credential reaches the intended admin view. |
| PRD-AC-11 | Account data and balances remain consistent across supported product surfaces. |
| PRD-AC-12 | Completed financial operations reconcile with transaction history where history is available. |
| PRD-AC-13 | Failed financial operations do not leave partial balance updates. |
| PRD-AC-14 | Unauthenticated users cannot use protected banking functionality as an authenticated user. |
| PRD-AC-15 | Logout terminates the authenticated experience. |
| PRD-AC-16 | The product provides understandable validation and error feedback. |
| PRD-AC-17 | Core login and banking controls are usable through supported accessible interaction patterns. |

## 22. Out-of-Scope Assumptions

- This PRD does not assume undocumented banking products such as cards, mortgages, investments or bill pay unless they are visibly present in the live application.
- This PRD does not prescribe a fixed sequence of user actions.
- This PRD does not define automation implementation, selectors, APIs or framework-specific behavior.
- Where a feature is conditionally present in the live UI, its current live behavior is authoritative.

## 23. Source and Evidence Notes

The public QA Playground website describes the Bank Demo as a full simulated banking app covering login, accounts, dashboard and transaction management. The Demo Apps page further describes it as a practice environment with forms, validations and account workflows.

The complete credential table in Section 2 is taken directly from the login-page screenshot supplied for this PRD: standard_user, locked_user, frozen_user, overdraft_user, slow_user, error_user and admin_user, including their displayed passwords and descriptions.

Final product principle: This document specifies what the Bank Demo is expected to provide and how its product states should behave. It intentionally does not prescribe example user journeys; scenarios should be derived from these product requirements.

*End of Product Requirements Document*
