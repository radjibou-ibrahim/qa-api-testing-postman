# API Documentation Analysis

## 1. Overview

This document contains the API analysis performed before designing and executing the API test cases.

The API selected for this project is ReqRes, a hosted REST API designed for testing, QA automation and development purposes.

The API provides authentication and user management endpoints that allow QA engineers to practice REST API testing using tools such as Postman.

The official documentation is available at:

https://reqres.in/docs

---

## 2. API Base URL
```text 
https://reqres.in
```
For the user management endpoints used in this project:

```text 
{{base_url}}/api
```

Example:

```text
{{base_url}}/api/users
```
---

## 3. Authentication

The current ReqRes API requires an API key for API requests.

The API key is sent through the following HTTP header:

```text 
x-api-key: {{api_key}}
```

The API key must not be committed to the public GitHub repository.

Postman environment variables are used to manage sensitive configuration values.
Expected behavior will be verified during test execution.

Example:
```text
base_url = https://reqres.in
api_key = <local-secret-value>
```
---

## 4. HTTP Methods

The API uses standard HTTP methods.

| HTTP Method | Purpose |
|---|---|
| GET | Retrieve resources |
| POST | Create resources |
| PUT | Update resources |
| PATCH | Partially update resources |
| DELETE | Delete resources |

---

## 5. Authentication Endpoints

POST /api/login

Used to test the login functionality.

POST {{base_url}}/api/login

Example request body:
```text
{
  "email": "eve.holt@reqres.in",
  "password": "pistol"
}
```

Expected successful response:

```text
200 OK
```

The response contains an authentication token.

---

### Negative Login Testing

The following situations will be tested:

- Missing password
- Invalid credentials
- Missing email
- Invalid email format
- Empty request body

Expected behavior will be verified against the actual API response.

---

## 6. User Endpoints

### GET /api/users

- retrieves a list of users
- retrieves a specific user

Negative testing will include an invalid or non-existing user ID.

---

### POST /api/users
- creates a new user
---

### PUT /api/users/{id}
- updates an existing user

---

### PATCH /api/users/{id}
- performs a partial update of a user.
  
---

### DELETE /api/users/{id}

- deletes a user.

---

## 7. Response Validation

API responses will be validated using Postman assertions.

The following elements will be checked:

- HTTP status code
- Response body
- JSON structure
- Required fields
- Data types
- Returned values
- Authentication token
- Response headers
- Content-Type
- Response time

---

## 8. Data Validation

For user responses, relevant fields may include:

id
email
first_name
last_name
avatar

The tests will verify that the returned data follows the expected response structure.

---

## 9. Error Handling

Negative tests will verify how the API handles invalid requests.

Examples include:

- Invalid credentials
- Missing required data
- Invalid user ID
- Invalid endpoint
- Empty request body
- Invalid request format
- Missing or invalid authentication

The actual API response will be recorded during test execution.

---

## 10. Pagination

The user list endpoint supports pagination.
```text
Example:

GET {{base_url}}/api/users?page=2
```
Pagination-related information will be validated, including:

- Current page
- Number of users per page
- Total number of users
- Total number of pages
- Returned user collection

---

## 11. API Testing Scope

The API testing scope includes:

### Functional Testing

- Authentication
- User retrieval
- User creation
- User update
- Partial update
- User deletion

### Negative Testing

- Invalid credentials
- Missing fields
- Invalid user ID
- Invalid endpoint
- Invalid request data

### Validation Testing

- Status codes
- Response structure
- Response fields
- Data types
- Headers
- Response time

### ### API Test Automation

- Postman assertions
- Environment variables
- Collection Runner
- Newman execution

---

## 12. Out of Scope

The following areas are outside the initial scope of this project:

- Performance/load testing
- Stress testing
- Penetration testing
- Infrastructure testing
- Database testing
- Production monitoring
- Real user data testing

---

## 13. QA Objective

The main QA objective is to determine whether the API behaves according to the documented contract and whether it correctly handles valid and invalid requests.

Testing will be based on observed API behavior, and actual execution results will be documented after the Postman collection has been executed.

---

## 14. Source

Official ReqRes API documentation:

https://reqres.in/docs
