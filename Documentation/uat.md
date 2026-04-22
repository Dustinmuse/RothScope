# User Acceptance Testing (UAT)

## Last Updated: 2026-04-21

---

# 1. Feature Overview

| Feature               | Priority | Iteration | Client Facing (Y/N) |
| --------------------- | -------- | --------- | ------------------- |
| Client Creation       | High     | 2         | Y                   |
| Scenario Creation     | High     | 2         | Y                   |
| Asset Creation        | High     | 2         | Y                   |
| Assumption Creation   | High     | 3         | Y                   |
| Calculations          | High     | 4         | Y                   |
| Advisors              | Low      | 4         | N                   |
| Income                | Medium   | 4         | Y                   |
| Optimization Workflow | High     | 5         | N                   |
| Save Optimization     | Medium   | 4         | Y                   |
| Login                 | Medium   | 3         | Y                   |

---

# 2. Acceptance Scenarios

## Feature: Client Creation

### Scenario 1: Successfully creating a client

**Given:**

A general user

**When:**

When they create a client

**Then:**

The client is created and stored in the Moneytree database

**Status:** (Not Tested / Internal Passed / Client Accepted)

Client Accepted

**Evidence:** (link to PR, test file, video, screenshot)

![Creating client image](/Documentation/UAT%20Screenshots/CreatingClient.png)
![Client created image](/Documentation/UAT%20Screenshots/ClientCreated.png)

### Scenario 2: Error Handling

**Given:**

A general user

**When:**

When they create a client where required fields are not filled out

**Then:**

The user would receive an error message on the UI

**Status:**

Internal Passed

**Evidence:**

![Creating client error image](/Documentation/UAT%20Screenshots/CreatingClientError.png)

### Scenario 3: Edge Case

**Given:**

A general user

**When:**

A interrupted connection to the api/database

**Then:**

The user would receive an error message on the UI stating an internal server error

**Status:**

Internal Passed

**Evidence:**

![Internal server error when creating a client image](/Documentation/UAT%20Screenshots/CreatingClientEdgeCase.png)

---

## Feature: Scenario Creation

### Scenario 1: Successfully creating a scenario

**Given:**

A general user

**When:**

When they create a scenario

**Then:**

The scenario is created and stored in the Moneytree database

**Status:**

Client Passed

**Evidence:**

![Creating scenario image](/Documentation/UAT%20Screenshots/CreatingScenario.png)
![Scenario created image](/Documentation/UAT%20Screenshots/ScenarioCreated.png)

### Scenario 2: Error Handling

**Given:**

A general user

**When:**

When they create a scenario with no name

**Then:**

The user would receive an error message on the UI

**Status:**

Internal Passed

**Evidence:**

![Creating scenario error image](/Documentation/UAT%20Screenshots/CreatingScenarioError.png)

### Scenario 3: Edge Case

**Given:**

A general user

**When:**

When they create a new scenario with special characters in the name

**Then:**

The scenario saves successfully without throwing an internal server error

**Status:**

Internal Passed

**Evidence:**

![Creating scenario edge case image](/Documentation/UAT%20Screenshots/CreatingScenarioEdgeCase.png)

---

## Feature: Asset Creation

### Scenario 1: Successfully creating an asset

**Given:**

A general user

**When:**

When they create an asset

**Then:**

The asset is created and stored in the Moneytree database

**Status:**

Client Passed

**Evidence:**

![Creating asset image](/Documentation/UAT%20Screenshots/CreatingAsset.png)
![Asset created image](/Documentation/UAT%20Screenshots/AssetCreated.png)

### Scenario 2: Error Handling

**Given:**

A general user

**When:**

When they attempt to create an asset without entering a required name

**Then:**

The user would receive an error message on the UI

**Status:**

Internal Passed

**Evidence:**

![Creating asset error image](/Documentation/UAT%20Screenshots/CreatingAssetError.png)

### Scenario 3: Edge Case

**Given:**

A general user

**When:**

When they create a new asset with special characters in the name

**Then:**

The system handles the input gracefully and saves it accurately without data corruption

**Status:**

Internal Passed

**Evidence:**

![Creating asset edge case image](/Documentation/UAT%20Screenshots/CreatingAssetEdgeCase.png)

---

## Feature: Assumption Creation

### Scenario 1: Successfully creating assumptions

**Given:**

A general user

**When:**

When they create assumptions and provide a retirement age and life expectancy

**Then:**

The assumptions are stored in the Moneytree database and associated with the selected scenario/client

**Status:** (Not Tested / Internal Passed / Client Accepted)

Client Accepted

**Evidence:**

<img width="1408" height="837" alt="scenario_creation_1" src="https://github.com/user-attachments/assets/1b11c421-14a2-4e3b-b0db-aae690615c20" />

<img width="1412" height="837" alt="scenario_creation_1_2" src="https://github.com/user-attachments/assets/e7a1beb3-3c83-49ff-9a7a-9f704730e6e6" />


### Scenario 2: Error Handling

**Given:**

A general user

**When:**

When they attempt to save assumptions with required fields missing (retirement age or life expectancy)

**Then:**

The user receives a validation error on the UI and the assumptions are not saved

**Status:**

Internal Passed

**Evidence:**

<img width="1410" height="837" alt="assumption_creation_2" src="https://github.com/user-attachments/assets/2acbb325-39fb-4287-950a-d1beccd83c5e" />


### Scenario 3: Edge Case

**Given:**

A general user

**When:**

When they enter a retirement age that is less than the current age, or a life expectancy that is less than the retirement age

**Then:**

The system shows a validation error preventing save and guides the user to correct the values

**Status:**

Internal Passed

**Evidence:**

---

<img width="1410" height="840" alt="assumption_creation_3" src="https://github.com/user-attachments/assets/69bf07f0-5232-4795-87ff-3c4cd7428fb8" />


## Feature: Save Optimization

### Scenario 1: Successfully saving an optimization

**Given:**

A general user with a prepared scenario and valid inputs

**When:**

When they run a save optimization process and choose to save the optimization results with a name

**Then:**

The optimization completes, results are stored in the Moneytree database, and the saved optimization is associated with the selected scenario/client and visible in the UI

**Status:** (Not Tested / Internal Passed / Client Accepted)

Client Accepted

**Evidence:** 

<img width="1918" height="837" alt="saving_1" src="https://github.com/user-attachments/assets/df90446f-320e-4ceb-a91e-edc8a5579b04" />

<img width="1917" height="837" alt="saving_1_2" src="https://github.com/user-attachments/assets/22c78d27-e2ef-458e-8caf-93140cc4600f" />

<img width="1918" height="840" alt="saving_2" src="https://github.com/user-attachments/assets/1c5627df-efa3-4ec5-8e57-26d210cb2c8b" />


### Scenario 2: Error Handling

**Given:**

A general user

**When:**

When they attempt to save optimization results without providing a required name or required inputs

**Then:**

The user receives a validation error on the UI and the optimization is not saved

**Status:**

Internal Passed

**Evidence:**

### Scenario 3: Edge Case

**Given:**

A general user

**When:**

When the optimization service fails or returns partial results (e.g., timeout, server error) during save

**Then:**

The system shows a clear error, does not create a corrupted save, and offers retry or export of partial results; audit logs capture the failure

**Status:**

Internal Passed

**Evidence:**

<img width="1918" height="836" alt="saving_3" src="https://github.com/user-attachments/assets/4d02a550-2881-4f0d-b8fb-8f4e77526ae1" />


---

## Feature: Roth Optimization Workflow

### Scenario 1: Successfully completing Roth optimization workflow

**Given:**

A registered user with a valid scenario, account balances, and required assumptions

**When:**

They start the Roth optimization workflow, provide required inputs (tax assumptions, targets), and run the workflow to completion

**Then:**

The workflow produces recommended conversion/optimization actions, results are saved to the Moneytree database, a report is generated, and the user can accept/apply the recommendations

**Status:**

Client Accepted

**Evidence:**

### Scenario 2: Error Handling

**Given:**

A registered user

**When:**

They run the Roth optimization workflow with missing or invalid inputs, or when business rules conflict (e.g., requested conversion exceeds available balance)

**Then:**

The system shows validation errors or business-rule warnings, prevents destructive actions, and does not apply recommendations until corrected

**Status:**

Internal Passed

**Evidence:**

### Scenario 3: Edge Case

**Given:**

A registered user

**When:**

The user attempts a long-running multi-step Roth optimization (multiple conversions, tax-year distribution) and the network or service is interrupted mid-process

**Then:**

The system handles the interruption safely: partial changes are not applied, the process can be resumed or rolled back, and the user is presented with the current workflow state and guidance

**Status:**

Internal Passed

**Evidence:**

---

## Income Creation

### Scenario 1: Successfully creating income

**Given:**

A general user

**When:**

When they create income with yearly income and personal income fields populated

**Then:**

The income entries are created and stored in the Moneytree database

**Status:**

Client Passed

**Evidence:**

<img width="1903" height="841" alt="income_1" src="https://github.com/user-attachments/assets/8b9c60e3-fa73-4298-860d-ffde8de23039" />

<img width="1900" height="843" alt="income_1_2" src="https://github.com/user-attachments/assets/7e9456e6-a534-411f-a5c0-3213406afbcb" />


### Scenario 2: Error Handling

**Given:**

A general user

**When:**

When they attempt to save income without required numeric values or with non-numeric input

**Then:**

The user receives a validation error on the UI and the income is not saved

**Status:**

Internal Tested

**Evidence:**

<img width="1901" height="837" alt="income_2" src="https://github.com/user-attachments/assets/d8a93942-c808-4677-8650-7df839d72094" />


### Scenario 3: Edge Case

**Given:**

A general user

**When:**

When they enter decimal values, extremely large values, or zero/negative income

**Then:**

The system validates numeric ranges, rejects invalid negative values, and correctly stores valid decimals and large numbers without data corruption

**Status:**

Internal Tested

**Evidence:**

<img width="1897" height="841" alt="income_3" src="https://github.com/user-attachments/assets/f0d4ade8-e95d-4b74-ad1d-c3837dc066aa" />

---

## Feature: Login

### Scenario 1: Successfully logging in

**Given:**

A registered user

**When:**

They enter valid username and password and submit the login form

**Then:**

They are authenticated, receive a valid session/token, and are redirected to the application dashboard

**Status:**

Client Accepted

**Evidence:**

<img width="1901" height="837" alt="login_1" src="https://github.com/user-attachments/assets/93ec37e4-8dc9-4bd5-a301-b00124841c49" />

<img width="1913" height="861" alt="login_1_2" src="https://github.com/user-attachments/assets/a28e2256-84a6-4fbf-bf45-0c7143f852b8" />


### Scenario 2: Error Handling

**Given:**

Any user

**When:**

They submit the login form with an empty username or password, or incorrect credentials

**Then:**

The user receives an appropriate error message and is not authenticated

**Status:**

Internal Tested

**Evidence:**

<img width="1900" height="833" alt="login_2" src="https://github.com/user-attachments/assets/83ceabb5-4b47-404b-b1a3-75a412e7a7a6" />


### Scenario 3: Edge Case

**Given:**

Any user

**When:**

They enter credentials with leading/trailing whitespace, special characters, or attempt repeated invalid logins

**Then:**

Input is trimmed/validated, special characters are handled safely, and the system enforces rate-limiting/account lockout policies for repeated failures

**Status:**

Internal Tested

**Evidence:**

<img width="1900" height="838" alt="login_2" src="https://github.com/user-attachments/assets/6953bfae-ceaa-4b15-8925-0aeb4723ec29" />


---

# 3. Client UAT Log

These tests are validated by the client.

| Date       | Feature           | Client Feedback                      | Action Required                                   | Resolved (Y/N) |
| ---------- | ----------------- | ------------------------------------ | ------------------------------------------------- | -------------- |
| 2026-02-16 | Client Creation   | Simplify co-client form behavior     | Replace "Include Co-client" with "Married" toggle | Y              |
| 2026-02-16 | Scenario Creation | Need a way to add assumptions/Income | Add a form for assumptions and income in the UI   | Y              |
| 2026-02-16 | Asset Creation    | Simplify asset summary and form      | Redesign UI for assets and the form for assets    | Y              |

---

# 4. Open Acceptance Risks

## Risk1

- Risk: Direct API manipulation could bypass client-side validation for Client, Scenario, or Asset creation and inject malformed data into the database.
- Mitigation Plan: Maintain request validation on the backend API layer before database insertion.

## Risk2

- Risk: Background silent login tokens might fail to renew if the user temporarily loses internet connection while making changes, resulting in an ungraceful logout and unsaved work on these forms.
- Mitigation Plan: Cache form states locally before attempting API calls, which permanently discard the form data.
