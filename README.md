# API Testing with Postman – User Management System 
## Postman 
## REST API
## JavaScript
## Newman
## QA

### Project Overview

This project is a portfolio-based REST API testing project designed to demonstrate practical QA skills using Postman.

The project focuses on testing a user management API covering authentication, user management operations, positive and negative testing, automated assertions, test execution and reporting.

The objective is to simulate a realistic QA workflow for an API-based application.

---

## Project Objectives

The main objectives of this project are to:

- Analyze REST API endpoints and requirements
- Design API test scenarios and test cases
- Test authentication workflows
- Validate CRUD operations
- Perform positive and negative testing
- Validate HTTP status codes
- Validate JSON response structures
- Validate response data
- Implement automated assertions using JavaScript
- Use Postman environment variables
- Execute collections using Postman Collection Runner
- Execute API tests using Newman
- Generate test execution reports
- Document defects found during testing
- Maintain traceability between requirements, test scenarios, test cases and defects

---

## Application Under Test

The project uses ReqRes, a public REST API designed for testing and demonstration purposes.

The API provides endpoints that allow QA engineers to practice:

- Authentication
- User retrieval
- User creation
- User updates
- User deletion
- Error handling

### API

### ReqRes

https://reqres.in

«Note: ReqRes is a public demonstration API. API behavior and authentication requirements may change over time. Test results in this repository will reflect the behavior observed during the actual test execution.»

---

## Tools & Technologies

| Tool / Technology | Purpose |
|---|---|
| Postman | API requests and test automation |
| JavaScript | Postman test scripts and assertions |
| Newman | Command-line collection execution |
| GitHub | Version control and project documentation |
| Markdown | QA documentation |
| REST API | Application interface under test |
| JSON | Request and response data |

---

## Authentication Testing

Authentication testing covers scenarios such as:

- Login with valid credentials
- Login with invalid credentials
- Login with missing credentials
- Invalid authentication data
- Token validation
- Authentication-related error responses

Example workflow:
```text 
Valid Credentials
       ↓
POST /api/login
       ↓
Authentication
       ↓
Token
```
---

## User Management – CRUD Testing

The project covers the main CRUD operations:

Operation| HTTP Method| Purpose
Create| POST| Create a user
Read| GET| Retrieve users
Update| PUT| Update a user
Partial Update| PATCH| Partially update a user
Delete| DELETE| Delete a user

---

## Testing Approach

The following testing approaches and techniques are applied where appropriate:

### Positive Testing

Valid inputs and expected user actions are used to verify normal API behavior.

### Negative Testing

Invalid inputs, missing data and invalid requests are used to verify error handling.

### Boundary Value Analysis

Values around relevant boundaries are tested when applicable.

### Equivalence Partitioning

Input data is divided into representative valid and invalid classes.

### Functional Testing

API functionality is validated against the expected behavior.

### Exploratory Testing

Additional API behavior and potential risks are explored beyond predefined test cases.

### Regression Testing

Previously tested API functionality can be re-executed after changes.

### Retesting

Previously reported defects can be tested again after a fix is provided.

---

## Test Coverage

The project is planned to cover:

- Authentication
- User retrieval
- User creation
- User update
- Partial user update
- User deletion
- Invalid user IDs
- Missing request fields
- Invalid credentials
- Invalid endpoints
- Response validation
- Status code validation
- JSON structure validation
- Response time validation
- Authentication validation

---

## Postman Test Automation

Postman tests are implemented using JavaScript assertions.

Examples include:
```text 
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

Response validation:

pm.test("Response contains data", function () {
    const response = pm.response.json();

    pm.expect(response).to.have.property("data");
});
```
Response time validation:

```text 
pm.test("Response time is less than 1000ms", function () {
    pm.expect(pm.response.responseTime).to.be.below(1000);
});
```
---

## Environment Variables

The Postman environment uses variables such as:

- base_url
- api_key
- user_id
- created_user_id
- token
- environment

Example:
```text 
{{base_url}}/api/users/{{user_id}}
```
Sensitive values such as API keys are not committed to the public repository.

---

## End-to-End API Workflow

The project includes an end-to-end user management workflow:
```text 
Login
  ↓
Get Users
  ↓
Get Single User
  ↓
Create User
  ↓
Update User
  ↓
Partial Update
  ↓
Delete User
```

This workflow demonstrates how individual API requests can be combined into a complete functional flow.

---

## Test Execution

Test execution is performed using:

- Postman
- Postman Collection Runner
- Newman

Each test execution records relevant information such as:

- Test Case ID
- Expected Result
- Actual Result
- Status
- Execution Date
- Environment
- Evidence
- Related Defect ID

Possible execution statuses:

- PASS
- FAIL
- BLOCKED
- NOT RUN

---

## Defect Reporting

Defects identified during testing are documented using a structured bug report format.

Each defect may include:

- Bug ID
- Summary
- Endpoint
- Environment
- Preconditions
- Steps to Reproduce
- Expected Result
- Actual Result
- Severity
- Priority
- Evidence
- Status

---

## Test Reporting

Newman is used to execute the Postman collection from the command line and generate test execution reports.

Example:

newman run User-Management-API.postman_collection.json

HTML reporting:
```text 
newman run User-Management-API.postman_collection.json \
-r cli,html
```
The final execution results will be documented in the "09-Reports/" directory.

---

## Project Structure
```text 
qa-api-testing-postman/
│
├── README.md
│
├── 01-API-Analysis/
│   ├── API-Documentation.md
│   ├── Endpoint-Matrix.md
│   └── API-Risks.md
│
├── 02-Test-Plan/
│   └── Test-Plan.md
│
├── 03-Test-Scenarios/
│   └── Test-Scenarios.md
│
├── 04-Test-Cases/
│   └── Test-Cases.md
│
├── 05-Test-Data/
│   └── Test-Data.md
│
├── 06-Postman/
│   ├── Collections/
│   │   └── User-Management-API.postman_collection.json
│   │
│   └── Environments/
│       └── QA-API-Environment.postman_environment.json
│
├── 07-Test-Execution/
│   └── Test-Execution.md
│
├── 08-Bug-Reports/
│   └── Bug-Reports.md
│
├── 09-Reports/
│   ├── Newman-Report.html
│   └── Execution-Summary.md
│
├── 10-Evidence/
│   └── README.md
│
└── 11-Test-Summary/
    └── Test-Summary.md
```
---

## Traceability

Traceability is maintained throughout the testing process:

Requirement
     ↓
Test Scenario
     ↓
Test Case
     ↓
Postman Request
     ↓
Test Execution
     ↓
Defect

This provides visibility into test coverage and the impact of identified defects.

---

## Skills Demonstrated

This project demonstrates practical skills in:

- API Testing
- REST API
- Postman
- HTTP Methods
- JSON
- HTTP Status Codes
- Authentication Testing
- CRUD Testing
- Positive Testing
- Negative Testing
- Functional Testing
- Exploratory Testing
- Test Design
- JavaScript Assertions
- Environment Variables
- Test Automation Basics
- Collection Runner
- Newman
- Defect Reporting
- Test Reporting
- Jira
- GitHub
- QA Documentation

---

## Author

### Radjibou IBRAHIM

QA Junior / Manual QA Tester

This project is part of my QA portfolio and demonstrates practical API testing skills using Postman and Newman.
