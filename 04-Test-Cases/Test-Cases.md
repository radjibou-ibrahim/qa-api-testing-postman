# API Test Cases — User Management System

## 1. Purpose

This document contains the detailed test cases designed for the User Management REST API.

The test cases are derived from:

- API Documentation
- Endpoint Matrix
- API Risks
- Test Plan
- Test Scenarios

The objective is to verify the functional behavior, validation, error handling and basic response quality of the API.

---

## 2. Test Case Identification

Each test case has a unique identifier.

The following naming convention is used:

TC-AUTH-XXX
TC-GET-XXX
TC-POST-XXX
TC-PUT-XXX
TC-PATCH-XXX
TC-DELETE-XXX
TC-VAL-XXX

Where:

- "TC" = Test Case
- "AUTH" = Authentication
- "GET" = GET operations
- "POST" = POST operations
- "PUT" = PUT operations
- "PATCH" = PATCH operations
- "DELETE" = DELETE operations
- "VAL" = Response validation
- "XXX" = Sequential number

---

## 3. Test Case Fields

Each test case contains:

| Field | Description |
|---|---|
| Test Case ID | Unique test identifier |
| Scenario ID | Related test scenario |
| Endpoint | API endpoint under test |
| Method | HTTP method |
| Title | Test objective |
| Priority | Test importance |
| Preconditions | Conditions required before execution |
| Test Data | Input data required |
| Steps | Actions performed |
| Expected Result | Expected API behavior |
| Actual Result | Observed behavior |
| Status | PASS / FAIL / BLOCKED / NOT RUN |
| Evidence | Supporting evidence |
| Defect ID | Related defect, if applicable |

---

## 4. Authentication Test Cases

TC-AUTH-001 — Login with valid credentials

Scenario ID: API-SC-001

Endpoint: "POST /api/login"

Priority: High

Preconditions

- API is accessible.
- Valid API key is available.
- Valid login credentials are available.

Test Data
```text
{
  "email": "eve.holt@reqres.in",
  "password": "pistol"
}
```
Steps

1. Open Postman.
2. Select "POST /api/login".
3. Add the required API key header.
4. Enter the valid credentials in the request body.
5. Send the request.

Expected Result

- API returns a successful response.
- HTTP status code is "200 OK".
- Response contains an authentication token.

Actual Result

Not Run

Status

NOT RUN

---

TC-AUTH-002 — Login with invalid credentials

Scenario ID: API-SC-002

Endpoint: "POST /api/login"

Priority: High

Preconditions

- API is accessible.
- API key is available.

Test Data

{
  "email": "invalid@test.com",
  "password": "invalidPassword"
}

Steps

1. Send a POST request to "/api/login".
2. Provide invalid login credentials.
3. Send the request.

Expected Result

- API rejects the authentication request.
- An appropriate error response is returned.

Actual Result

Not Run

Status

NOT RUN

---

TC-AUTH-003 — Login without password

Scenario ID: API-SC-003

Endpoint: "POST /api/login"

Priority: High

Test Data

{
  "email": "eve.holt@reqres.in"
}

Steps

1. Send a POST request to "/api/login".
2. Provide a valid email.
3. Do not provide the password.
4. Send the request.

Expected Result

The API rejects the request and returns an appropriate validation error.

Actual Result

Not Run

Status

NOT RUN

---

TC-AUTH-004 — Login without email

Scenario ID: API-SC-004

Endpoint: "POST /api/login"

Priority: High

Test Data

{
  "password": "pistol"
}

Steps

1. Send a POST request to "/api/login".
2. Provide the password.
3. Do not provide the email.
4. Send the request.

Expected Result

The API rejects the request and returns an appropriate validation error.

Actual Result

Not Run

Status

NOT RUN

---

TC-AUTH-005 — Login with empty request body

Scenario ID: API-SC-005

Endpoint: "POST /api/login"

Priority: Medium

Test Data

{}

Steps

1. Send a POST request to "/api/login".
2. Use an empty JSON body.
3. Send the request.

Expected Result

The API rejects the request with an appropriate error response.

Actual Result

Not Run

Status

NOT RUN

---

TC-AUTH-006 — Request without API key

Scenario ID: API-SC-007

Endpoint: API endpoint requiring authentication

Priority: High

Preconditions

- API is accessible.

Steps

1. Select a protected API request.
2. Remove the "x-api-key" header.
3. Send the request.

Expected Result

The API rejects the request with an appropriate authentication or authorization response.

Actual Result

Not Run

Status

NOT RUN

---

TC-AUTH-007 — Request with invalid API key

Scenario ID: API-SC-008

Endpoint: API endpoint requiring authentication

Priority: High

Test Data

x-api-key: invalid-api-key

Steps

1. Select a protected API request.
2. Provide an invalid API key.
3. Send the request.

Expected Result

The API rejects the request with an appropriate authentication or authorization response.

Actual Result

Not Run

Status

NOT RUN

---

5. GET User Test Cases

TC-GET-001 — Retrieve users successfully

Scenario ID: API-SC-009

Endpoint: "GET /api/users"

Priority: High

Preconditions

- API is accessible.
- Valid API key is available.

Steps

1. Send a GET request to "/api/users".
2. Provide the required authentication.
3. Send the request.

Expected Result

- HTTP status code is "200 OK".
- Response contains a collection of users.

Actual Result

Not Run

Status

NOT RUN

---

TC-GET-002 — Retrieve users using pagination

Scenario ID: API-SC-010

Endpoint: "GET /api/users?page=2"

Priority: Medium

Steps

1. Send a GET request to "/api/users?page=2".
2. Send the request.

Expected Result

- HTTP status code is "200 OK".
- Response contains user data.
- Pagination information is returned.

Actual Result

Not Run

Status

NOT RUN

---

TC-GET-003 — Retrieve user using valid ID

Scenario ID: API-SC-011

Endpoint: "GET /api/users/{id}"

Priority: High

Test Data

user_id = 2

Steps

1. Send a GET request to "/api/users/2".
2. Send the request.

Expected Result

- HTTP status code is "200 OK".
- The requested user is returned.
- The returned user ID matches the requested ID.

Actual Result

Not Run

Status

NOT RUN

---

TC-GET-004 — Retrieve non-existing user

Scenario ID: API-SC-012

Endpoint: "GET /api/users/999"

Priority: Medium

Steps

1. Send a GET request to "/api/users/999".
2. Send the request.

Expected Result

The API returns an appropriate not-found response.

Actual Result

Not Run

Status

NOT RUN

---

TC-GET-005 — Retrieve user using invalid ID

Scenario ID: API-SC-013

Endpoint: "GET /api/users/{id}"

Priority: Medium

Test Data

user_id = invalid

Steps

1. Send a GET request using an invalid user ID.
2. Send the request.

Expected Result

The API handles the invalid user ID appropriately.

Actual Result

Not Run

Status

NOT RUN

---

TC-GET-006 — Validate user response structure

Scenario ID: API-SC-023

Endpoint: "GET /api/users/{id}"

Priority: Medium

Steps

1. Send a GET request for a valid user.
2. Inspect the JSON response.
3. Validate the returned user structure.

Expected Result

The response contains the expected user properties and appropriate data types.

Actual Result

Not Run

Status

NOT RUN

---

## 6. CREATE User Test Cases

TC-POST-001 — Create user with valid data

Scenario ID: API-SC-014

Endpoint: "POST /api/users"

Priority: High

Test Data

{
  "name": "John QA",
  "job": "QA Tester"
}

Steps

1. Select "POST /api/users".
2. Add the required headers.
3. Enter valid user data.
4. Send the request.

Expected Result

- HTTP status code is "201 Created".
- Response contains the created user information.
- A user ID is returned.
- A creation timestamp is returned where provided by the API.

Actual Result

Not Run

Status

NOT RUN

---

TC-POST-002 — Create user with missing name

Scenario ID: API-SC-015

Endpoint: "POST /api/users"

Priority: Medium

Test Data
```text
{
  "job": "QA Tester"
}
```
Steps

1. Send a POST request to "/api/users".
2. Remove the "name" field.
3. Send the request.

Expected Result

The API validates the request according to the API contract.

Actual Result

Not Run

Status

NOT RUN

---

TC-POST-003 — Create user with missing job

Scenario ID: API-SC-016

Endpoint: "POST /api/users"

Priority: Medium

Test Data
```text
{
  "name": "John QA"
}
```
Steps

1. Send a POST request to "/api/users".
2. Remove the "job" field.
3. Send the request.

Expected Result

The API validates the request according to the API contract.

Actual Result

Not Run

Status

NOT RUN

---

TC-POST-004 — Create user with empty request body

Scenario ID: API-SC-017

Endpoint: "POST /api/users"

Priority: Medium

Test Data

{}

Steps

1. Send a POST request to "/api/users".
2. Use an empty request body.
3. Send the request.

Expected Result

The API handles the invalid request according to the API contract.

Actual Result

Not Run

Status

NOT RUN

---

TC-POST-005 — Validate created user response

Scenario ID: API-SC-014

Endpoint: "POST /api/users"

Priority: Medium

Steps

1. Create a user using valid data.
2. Inspect the response.
3. Validate the returned fields.

Expected Result

The response contains the expected user information and appropriate response fields.

Actual Result

Not Run

Status

NOT RUN

---

## 7. UPDATE User Test Cases

TC-PUT-001 — Update user with valid data

Scenario ID: API-SC-018

Endpoint: "PUT /api/users/{id}"

Priority: High

Test Data
```text
{
  "name": "Ahmed QA",
  "job": "Automation Tester"
}
```
Steps

1. Send a PUT request to "/api/users/2".
2. Provide valid updated user data.
3. Send the request.

Expected Result

- HTTP status code is "200 OK".
- The response contains the updated values.
- An updated timestamp is returned where provided by the API.

Actual Result

Not Run

Status

NOT RUN

---

TC-PUT-002 — Update user using non-existing ID

Scenario ID: API-SC-019

Endpoint: "PUT /api/users/{id}"

Priority: Medium

Test Data

user_id = 999

Steps

1. Send a PUT request using a non-existing user ID.
2. Provide valid update data.
3. Send the request.

Expected Result

The API handles the request according to the API contract.

Actual Result

Not Run

Status

NOT RUN

---

TC-PUT-003 — Validate updated user response

Scenario ID: API-SC-018

Endpoint: "PUT /api/users/{id}"

Priority: Medium

Steps

1. Update an existing user.
2. Inspect the response.
3. Compare the returned values with the submitted values.

Expected Result

The response contains the expected updated values.

Actual Result

Not Run

Status

NOT RUN

---

## 8. PATCH User Test Cases

TC-PATCH-001 — Partially update a user

Scenario ID: API-SC-020

Endpoint: "PATCH /api/users/{id}"

Priority: High

Test Data
```text
{
  "job": "Automation Tester"
}
```
Steps

1. Send a PATCH request to "/api/users/2".
2. Provide only the field to be updated.
3. Send the request.

Expected Result

- HTTP status code is "200 OK".
- The requested field is updated.
- The API processes the partial update successfully.

Actual Result

Not Run

Status

NOT RUN

---

## 9. DELETE User Test Cases

TC-DELETE-001 — Delete existing user

Scenario ID: API-SC-021
```text
Endpoint: "DELETE /api/users/{id}"
```
Priority: High

Test Data
```text
user_id = 2
```
Steps

1. Send a DELETE request to "/api/users/2".
2. Send the request.

Expected Result

- HTTP status code is "204 No Content".
- The response body is empty.

Actual Result

Not Run

Status

NOT RUN

---

TC-DELETE-002 — Delete user using non-existing ID

Scenario ID: API-SC-022

Endpoint: "DELETE /api/users/{id}"

Priority: Medium

Test Data

user_id = 999

Steps

1. Send a DELETE request to "/api/users/999".
2. Send the request.

Expected Result

The API handles the deletion request according to the API contract.

Actual Result

Not Run

Status

NOT RUN

---

## 10. Response Validation Test Cases

TC-VAL-001 — Validate HTTP status code

Scenario ID: API-SC-023

Endpoint: Applicable API endpoints

Priority: High

Steps

1. Execute the selected API request.
2. Verify the returned HTTP status code.
3. Compare it with the expected status code.

Expected Result

The API returns the expected HTTP status code for the executed operation.

Actual Result

Not Run

Status

NOT RUN

---

TC-VAL-002 — Validate Content-Type header

Scenario ID: API-SC-023

Endpoint: Applicable API endpoints

Priority: Medium

Steps

1. Execute an API request returning JSON.
2. Inspect the response headers.
3. Check the "Content-Type" header.

Expected Result

The response contains the expected JSON Content-Type.

Actual Result

Not Run

Status

NOT RUN

---

TC-VAL-003 — Validate response time

Scenario ID: API-SC-023

Endpoint: Applicable API endpoints

Priority: Low

Steps

1. Execute the API request.
2. Record the response time.
3. Compare the response time with the defined validation threshold.

Expected Result

The response time is below the defined threshold.

Actual Result

Not Run

Status

NOT RUN

---

TC-VAL-004 — Validate JSON data types

Scenario ID: API-SC-023

Endpoint: Applicable API endpoints

Priority: Medium

Steps

1. Execute a user retrieval request.
2. Parse the JSON response.
3. Validate the data types of relevant fields.

Expected Result

The returned fields use the expected data types.

Example:

id → number
email → string
first_name → string
last_name → string
avatar → string

Actual Result

Not Run

Status

NOT RUN

---

TC-VAL-005 — Validate response required fields

Scenario ID: API-SC-023

Endpoint: Applicable API endpoints

Priority: Medium

Steps

1. Execute the API request.
2. Inspect the JSON response.
3. Verify that expected properties are present.

Expected Result

Required response properties are present according to the API contract.

Actual Result

Not Run

Status

NOT RUN

---

## 11. Test Case Summary

| Test Case ID | Scenario ID | Test Case | Type | Priority | Status |
|---|---|---|---|---|---|
| TC-AUTH-001 | API-SC-001 | Login with valid credentials | Positive | High | NOT RUN |
| TC-AUTH-002 | API-SC-002 | Login with invalid credentials | Negative | High | NOT RUN |
| TC-AUTH-003 | API-SC-003 | Login without password | Negative | High | NOT RUN |
| TC-AUTH-004 | API-SC-004 | Login without email | Negative | High | NOT RUN |
| TC-AUTH-005 | API-SC-005 | Login with empty request body | Negative | Medium | NOT RUN |
| TC-AUTH-006 | API-SC-007 | Request without API key | Negative | High | NOT RUN |
| TC-AUTH-007 | API-SC-008 | Request with invalid API key | Negative | High | NOT RUN |
| TC-GET-001 | API-SC-009 | Retrieve users successfully | Positive | High | NOT RUN |
| TC-GET-002 | API-SC-010 | Retrieve users using pagination | Positive | Medium | NOT RUN |
| TC-GET-003 | API-SC-011 | Retrieve user using valid ID | Positive | High | NOT RUN |
| TC-GET-004 | API-SC-012 | Retrieve non-existing user | Negative | Medium | NOT RUN |
| TC-GET-005 | API-SC-013 | Retrieve user using invalid ID | Negative | Medium | NOT RUN |
| TC-GET-006 | API-SC-023 | Validate user response structure | Validation | Medium | NOT RUN |
| TC-POST-001 | API-SC-014 | Create user with valid data | Positive | High | NOT RUN |
| TC-POST-002 | API-SC-015 | Create user with missing name | Negative | Medium | NOT RUN |
| TC-POST-003 | API-SC-016 | Create user with missing job | Negative | Medium | NOT RUN |
| TC-POST-004 | API-SC-017 | Create user with empty request body | Negative | Medium | NOT RUN |
| TC-POST-005 | API-SC-014 | Validate created user response | Validation | Medium | NOT RUN |
| TC-PUT-001 | API-SC-018 | Update user with valid data | Positive | High | NOT RUN |
| TC-PUT-002 | API-SC-019 | Update user using non-existing ID | Negative | Medium | NOT RUN |
| TC-PUT-003 | API-SC-018 | Validate updated user response | Validation | Medium | NOT RUN |
| TC-PATCH-001 | API-SC-020 | Partially update a user | Positive | High | NOT RUN |
| TC-DELETE-001 | API-SC-021 | Delete existing user | Positive | High | NOT RUN |
| TC-DELETE-002 | API-SC-022 | Delete user using non-existing ID | Negative | Medium | NOT RUN |
| TC-VAL-001 | API-SC-023 | Validate HTTP status code | Validation | High | NOT RUN |
| TC-VAL-002 | API-SC-023 | Validate Content-Type header | Validation | Medium | NOT RUN |
| TC-VAL-003 | API-SC-023 | Validate response time | Non-functional | Low | NOT RUN |
| TC-VAL-004 | API-SC-023 | Validate JSON data types | Validation | Medium | NOT RUN |
| TC-VAL-005 | API-SC-023 | Validate response required fields | Validation | Medium | NOT RUN |

---

## 12. Test Case Statistics

Category| Number
Authentication| 7
GET| 6
POST| 5
PUT| 3
PATCH| 1
DELETE| 2
Response Validation| 5
Total| 30

---

## 13. Test Type Distribution

Test Type| Number
Positive| 10
Negative| 11
Validation| 8
Non-functional| 1
Total| 30

---

## 14. Priority Distribution

Priority| Number
High| 12
Medium| 17
Low| 1
Total| 30

---

## 15. Traceability

The test cases maintain traceability with the previously defined test scenarios.

Example:
```text 
API-SC-001
     ↓
TC-AUTH-001
     ↓
POST /api/login
     ↓
Postman Request
     ↓
Test Execution
     ↓
PASS / FAIL
     ↓
BUG-API-XXX

Another example:

API-SC-014
     ↓
TC-POST-001
     ↓
TC-POST-005
     ↓
POST /api/users
     ↓
Postman Tests
     ↓
Execution Result
```
---

## 16. Execution Status

All test cases are initially marked as:

NOT RUN

Actual results and final statuses will be recorded only after the test cases have been executed against the API.

Possible final statuses:

PASS
FAIL
BLOCKED
NOT RUN

---

## 17. Next Step

The next phase is:

### 05-Test-Data/
└── Test-Data.md

Test data will be prepared for:

- Authentication
- User creation
- User retrieval
- User updates
- Partial updates
- User deletion
- Negative testing
- API authentication
