# API Endpoint Matrix

## 1. Purpose

This document provides an overview of the API endpoints included in the testing scope.

The matrix is used to identify:

- Available endpoints
- HTTP methods
- Main functionality
- Authentication requirements
- Expected status codes
- Positive test coverage
- Negative test coverage

---

## 2. Authentication Endpoints

ID| Method| Endpoint| Purpose| Expected Success| Negative Testing
AUTH-001| POST| "/api/login"| Authenticate a user| 200| Yes

---

## 3. User Endpoints

ID| Method| Endpoint| Purpose| Expected Success| Negative Testing
USER-001| GET| "/api/users"| Retrieve users| 200| Yes
USER-002| GET| "/api/users/{id}"| Retrieve a specific user| 200| Yes
USER-003| POST| "/api/users"| Create a user| 201| Yes
USER-004| PUT| "/api/users/{id}"| Update a user| 200| Yes
USER-005| PATCH| "/api/users/{id}"| Partially update a user| 200| Yes
USER-006| DELETE| "/api/users/{id}"| Delete a user| 204| Yes

---

## 4. Detailed Endpoint Matrix

Endpoint| Method| Authentication| Request Body| Expected Status| Main Validations
"/api/login"| POST| API Key| JSON| 200| Token
"/api/login"| POST| API Key| JSON| 400| Error handling
"/api/users"| GET| API Key| None| 200| User list
"/api/users/{id}"| GET| API Key| None| 200| User data
"/api/users/{id}"| GET| API Key| None| 404| Error handling
"/api/users"| POST| API Key| JSON| 201| Created user
"/api/users/{id}"| PUT| API Key| JSON| 200| Updated user
"/api/users/{id}"| PATCH| API Key| JSON| 200| Partial update
"/api/users/{id}"| DELETE| API Key| None| 204| Empty response

---

## 5. HTTP Status Codes in Scope

Status Code| Meaning| Testing Purpose
200| OK| Successful retrieval/update/authentication
201| Created| Successful resource creation
204| No Content| Successful deletion
400| Bad Request| Invalid request data
401| Unauthorized| Authentication failure
404| Not Found| Resource does not exist

---

## 6. CRUD Coverage
```text
CREATE
POST /api/users
        ↓
READ
GET /api/users
GET /api/users/{id}
        ↓
UPDATE
PUT /api/users/{id}
PATCH /api/users/{id}
        ↓
DELETE
DELETE /api/users/{id}
```
---

7. Authentication Coverage
```text
API Key
   ↓
x-api-key
   ↓
API Request
   ↓
Response
```
Authentication-related tests will verify:

- Valid API key
- Missing API key
- Invalid API key
- Login with valid credentials
- Login with invalid credentials
- Missing login fields

---

## 8. Validation Coverage

Each endpoint may be tested for:

- Status code
- Response body
- JSON structure
- Required fields
- Data types
- Response headers
- Content-Type
- Response time
- Error messages

---

## 9. Traceability

Endpoint IDs will be used as a reference during test design.

Example:
```text
AUTH-001
   ↓
API-SC-001
   ↓
TC-AUTH-001
   ↓
Postman Request
   ↓
Test Execution
   ↓
BUG-API-001
```
This allows API requirements, test scenarios, test cases and defects to remain traceable throughout the project.

---

## 10. Matrix Status

Status: Initial analysis

The endpoint matrix will be updated if additional endpoints or test requirements are identified during the project.
