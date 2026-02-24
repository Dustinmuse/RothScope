# User Acceptance Testing (UAT)

## Last Updated: 2026-02-24

---

# 1. Feature Overview

| Feature           | Priority | Iteration | Client Facing (Y/N) |
| ----------------- | -------- | --------- | ------------------- |
| Client Creation   | High     | 2         | Y                   |
| Scenario Creation | High     | 2         | Y                   |
| Asset Creation    | High     | 2         | Y                   |

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
