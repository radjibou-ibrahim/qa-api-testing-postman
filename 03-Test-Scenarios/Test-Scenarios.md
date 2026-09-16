# API Test Scenarios — User Management System

## 1. Purpose

This document defines the test scenarios identified for the User Management REST API.

The scenarios are derived from:

- API documentation analysis
- Endpoint matrix
- API risks
- Test Plan
- Authentication requirements
- CRUD functionality
- Positive and negative testing needs

A test scenario describes what needs to be tested, while the detailed steps, test data and expected results will be defined later in the Test Cases document.

---

## 2. Scenario Identification

Each test scenario has a unique identifier using the following convention:

API-SC-XXX

Example:

API-SC-001

Where:

- "API" = API Testing Project
- "SC" = Scenario
- "XXX" = Sequential number

---

## 3. Authentication Scenarios

API-SC-001 — Login with valid credentials

Endpoint: "POST /api/login"

Type: Positive

Objective:

Verify that a user can successfully authenticate using valid credentials.

Expected outcome:

The API should return a successful HTTP response and provide an authentication token.

---

API-SC-002 — Login with invalid credentials

Endpoint: "POST /api/login"

Type: Negative

Objective:

Verify that the API rejects invalid authentication credentials.

Expected outcome:

The API should return an appropriate error response.

---

API-SC-003 — Login without password

Endpoint: "POST /api/login"

Type: Negative

Objective:

Verify that the API handles a login request when the password is missing.

Expected outcome:

The API should reject the request and return an appropriate validation error.

---

API-SC-004 — Login without email

Endpoint: "POST /api/login"

Type: Negative

Objective:

Verify that the API handles a login request when the email is missing.

Expected outcome:

The API should reject the request and return an appropriate validation error.

---

API-SC-005 — Login with empty request body

Endpoint: "POST /api/login"

Type: Negative

Objective:

Verify how the API handles a login request with an empty body.

Expected outcome:

The API should return an appropriate error response.

---

## 4. API Authentication Scenarios

API-SC-006 — Request with valid API key

Endpoint: API endpoints requiring authentication

Type: Positive

Objective:

Verify that an API request is successfully processed when a valid API key is provided.

Expected outcome:

The API should process the request successfully.

---

API-SC-007 — Request without API key

Endpoint: API endpoints requiring authentication

Type: Negative

Objective:

Verify how the API handles a request when the API key is missing.

Expected outcome:

The API should reject the request with an appropriate authentication or authorization response.

---

API-SC-008 — Request with invalid API key

Endpoint: API endpoints requiring authentication

Type: Negative

Objective:

Verify that an invalid API key is not accepted.

Expected outcome:

The API should reject the request with an appropriate authentication or authorization response.

---

## 5. GET User Scenarios

API-SC-009 — Retrieve users successfully

Endpoint: "GET /api/users"

Type: Positive

Objective:

Verify that the API successfully returns a list of users.

Expected outcome:

The API should return a successful response containing a user collection.

---

API-SC-010 — Retrieve users using pagination

Endpoint: "GET /api/users?page={page}"

Type: Positive

Objective:

Verify that the API correctly handles pagination parameters.

Expected outcome:

The response should contain the appropriate pagination information and user data.

---

API-SC-011 — Retrieve a user using a valid ID

Endpoint: "GET /api/users/{id}"

Type: Positive

Objective:

Verify that a specific user can be retrieved using a valid user ID.

Expected outcome:

The API should return a successful response containing the requested user.

---

API-SC-012 — Retrieve a non-existing user

Endpoint: "GET /api/users/{id}"

Type: Negative

Objective:

Verify how the API handles a request for a user that does not exist.

Expected outcome:

The API should return an appropriate not-found response.

---

API-SC-013 — Retrieve a user using an invalid ID

Endpoint: "GET /api/users/{id}"

Type: Negative

Objective:

Verify how the API handles an invalid user ID format or value.

Expected outcome:

The API should handle the invalid request appropriately.

---

## 6. CREATE User Scenarios

API-SC-014 — Create user with valid data

Endpoint: "POST /api/users"

Type: Positive

Objective:

Verify that a user can be created using valid user information.

Expected outcome:

The API should successfully create the user and return the appropriate response.

---

API-SC-015 — Create user with missing name

Endpoint: "POST /api/users"

Type: Negative

Objective:

Verify how the API handles a user creation request without the "name" field.

Expected outcome:

The API should validate the request according to the API contract.

---

API-SC-016 — Create user with missing job

Endpoint: "POST /api/users"

Type: Negative

Objective:

Verify how the API handles a user creation request without the "job" field.

Expected outcome:

The API should validate the request according to the API contract.

---

API-SC-017 — Create user with empty request body

Endpoint: "POST /api/users"

Type: Negative

Objective:

Verify how the API handles an empty request body during user creation.

Expected outcome:

The API should handle the invalid request according to the API contract.

---

## 7. UPDATE User Scenarios

API-SC-018 — Update user with valid data

Endpoint: "PUT /api/users/{id}"

Type: Positive

Objective:

Verify that an existing user can be updated using valid data.

Expected outcome:

The API should successfully process the update and return the appropriate response.

---

API-SC-019 — Update user using a non-existing ID

Endpoint: "PUT /api/users/{id}"

Type: Negative

Objective:

Verify how the API handles an update request targeting a non-existing user.

Expected outcome:

The API should handle the request according to the API contract.

---

## 8. PATCH User Scenarios

API-SC-020 — Partially update a user

Endpoint: "PATCH /api/users/{id}"

Type: Positive

Objective:

Verify that a specific user attribute can be updated without replacing the complete user data.

Expected outcome:

The API should successfully process the partial update.

---

## 9. DELETE User Scenarios

API-SC-021 — Delete an existing user

Endpoint: "DELETE /api/users/{id}"

Type: Positive

Objective:

Verify that an existing user can be deleted.

Expected outcome:

The API should return the appropriate successful deletion response.

---

API-SC-022 — Delete a user using a non-existing ID

Endpoint: "DELETE /api/users/{id}"

Type: Negative

Objective:

Verify how the API handles a deletion request targeting a non-existing user.

Expected outcome:

The API should handle the request according to the API contract.

---

## 10. Response Validation Scenarios

API-SC-023 — Validate API response structure and basic response quality

Endpoint: Applicable API endpoints

Type: Validation

Objective:

Verify that API responses follow the expected structure and basic quality criteria.

Expected outcome:

The response should:

- Return the expected HTTP status code
- Follow the expected JSON structure
- Contain required response properties
- Return appropriate data types
- Provide the expected Content-Type
- Respect the defined response-time validation threshold

---

## 11. Scenario Summary

| ID | Test Scenario | Type | Endpoint |
|---|---|---|---|
| API-SC-001 | Login with valid credentials | Positive | POST `/api/login` |
| API-SC-002 | Login with invalid credentials | Negative | POST `/api/login` |
| API-SC-003 | Login without password | Negative | POST `/api/login` |
| API-SC-004 | Login without email | Negative | POST `/api/login` |
| API-SC-005 | Login with empty request body | Negative | POST `/api/login` |
| API-SC-006 | Request with valid API key | Positive | API endpoints |
| API-SC-007 | Request without API key | Negative | API endpoints |
| API-SC-008 | Request with invalid API key | Negative | API endpoints |
| API-SC-009 | Retrieve users successfully | Positive | GET `/api/users` |
| API-SC-010 | Retrieve users using pagination | Positive | GET `/api/users` |
| API-SC-011 | Retrieve a user using a valid ID | Positive | GET `/api/users/{id}` |
| API-SC-012 | Retrieve a non-existing user | Negative | GET `/api/users/{id}` |
| API-SC-013 | Retrieve a user using an invalid ID | Negative | GET `/api/users/{id}` |
| API-SC-014 | Create user with valid data | Positive | POST `/api/users` |
| API-SC-015 | Create user with missing name | Negative | POST `/api/users` |
| API-SC-016 | Create user with missing job | Negative | POST `/api/users` |
| API-SC-017 | Create user with empty request body | Negative | POST `/api/users` |
| API-SC-018 | Update user with valid data | Positive | PUT `/api/users/{id}` |
| API-SC-019 | Update user using a non-existing ID | Negative | PUT `/api/users/{id}` |
| API-SC-020 | Partially update a user | Positive | PATCH `/api/users/{id}` |
| API-SC-021 | Delete an existing user | Positive | DELETE `/api/users/{id}` |
| API-SC-022 | Delete a user using a non-existing ID | Negative | DELETE `/api/users/{id}` |
| API-SC-023 | Validate API response structure and basic response quality | Validation | Applicable endpoints | 


---

## 12. Coverage Summary

Authentication

API-SC-001
API-SC-002
API-SC-003
API-SC-004
API-SC-005

5 scenarios

API Authentication

API-SC-006
API-SC-007
API-SC-008

3 scenarios

GET

API-SC-009
API-SC-010
API-SC-011
API-SC-012
API-SC-013

5 scenarios

POST

API-SC-014
API-SC-015
API-SC-016
API-SC-017

4 scenarios

PUT

API-SC-018
API-SC-019

2 scenarios

PATCH

API-SC-020

1 scenario

DELETE

API-SC-021
API-SC-022

2 scenarios

Response Validation

API-SC-023

1 scenario

---

## 13. Total

Total Test Scenarios: 23

Category| Number
Authentication| 5
API Authentication| 3
GET| 5
POST| 4
PUT| 2
PATCH| 1
DELETE| 2
Response Validation| 1
Total| 23

---

14. Traceability

The scenarios will be linked to the API analysis and risk assessment.

Example:

```text
API Endpoint
     ↓
API Risk
     ↓
API-SC-XXX
     ↓
Test Case
     ↓
Postman Request
     ↓
Execution Result
     ↓
Defect
```
Example:

```text 
POST /api/login
     ↓
RISK-001
     ↓
API-SC-001
     ↓
TC-AUTH-001
     ↓
Postman Login Request
     ↓
PASS / FAIL
     ↓
BUG-API-XXX
```

---

## 15. Scenario Status

Status: Ready for Test Case Design

The next phase is:

### 04-Test-Cases/
└── Test-Cases.md

Each scenario will be converted into one or more detailed test cases containing:

- Test Case ID
- Requirement / Endpoint
- Scenario ID
- Title
- Preconditions
- Test Data
- Steps
- Expected Result
- Priority
- Actual Result
- Status
- Evidence
- Related Defect ID
