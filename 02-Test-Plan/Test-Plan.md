# Test Plan — User Management API

## 1. Document Information

Field| Description
Project| User Management API Testing
Testing Type| API Testing
Application Under Test| ReqRes
Primary Tool| Postman
Automation Tool| Newman
Test Level| API / Integration
Environment| QA
Document Status| Draft
Version| 1.0

---

## 2. Project Overview

This Test Plan defines the strategy, scope, objectives and approach for testing the User Management REST API.

The API provides authentication and user management functionality.

The testing activities will focus on verifying that API endpoints behave as expected when receiving valid and invalid requests.

The project is designed as a practical QA portfolio project demonstrating API testing skills using Postman and Newman.

---

## 3. Test Objectives

The main objectives are to:

- Verify API functionality
- Validate authentication behavior
- Validate CRUD operations
- Verify HTTP status codes
- Validate response structures
- Validate response data
- Verify error handling
- Perform positive testing
- Perform negative testing
- Validate API response headers
- Perform basic response-time validation
- Implement automated assertions
- Execute API tests using Postman
- Execute the collection using Newman
- Generate test execution reports
- Identify and document defects
- Maintain test traceability

---

## 4. Scope

## 4.1 In Scope

The following functionality is included in the testing scope.

### Authentication

- Login with valid credentials
- Login with invalid credentials
- Missing authentication data
- Invalid authentication data
- API key validation

### User Management

- Retrieve all users
- Retrieve a specific user
- Create a user
- Update a user
- Partially update a user
- Delete a user

### Validation

- HTTP status codes
- Response body
- JSON structure
- Required fields
- Data types
- Response headers
- Content-Type
- Response time

### Negative Testing

- Invalid credentials
- Missing fields
- Empty request body
- Invalid user ID
- Invalid endpoint
- Missing API key
- Invalid API key
- Invalid request data

### Automation

- Postman test scripts
- JavaScript assertions
- Environment variables
- Collection Runner
- Newman execution
- Automated reporting

---

## 5. Out of Scope

The following activities are outside the scope of this project:

- Performance testing
- Load testing
- Stress testing
- Volume testing
- Penetration testing
- Full security assessment
- Infrastructure testing
- Database testing
- Production monitoring
- Mobile application testing
- UI testing
- Accessibility testing

Basic response-time assertions may be included, but they do not constitute a dedicated performance test.

---

## 6. Test Approach

The project follows a structured API testing approach.
```
API Analysis
     ↓
Test Planning
     ↓
Test Scenario Design
     ↓
Test Case Design
     ↓
Test Data Preparation
     ↓
Postman Collection
     ↓
Test Execution
     ↓
Defect Reporting
     ↓
Newman Execution
     ↓
Test Reporting
     ↓
Test Summary
```

Testing will combine predefined test cases with exploratory API testing where appropriate.

---

## 7. Testing Types

## 7.1 Functional Testing

Functional testing will verify that API endpoints perform their intended operations.

Examples:

- User creation
- User retrieval
- User update
- User deletion
- Login

---

## 7.2 Positive Testing

Valid inputs will be used to verify expected successful behavior.

Examples:

- Valid login credentials
- Valid user ID
- Valid user data
- Valid API key

---

## 7.3 Negative Testing

Invalid or incomplete inputs will be used to verify error handling.

Examples:

- Invalid credentials
- Missing fields
- Invalid user ID
- Invalid API key
- Empty request body
- Invalid endpoint

---

## 7.4 Validation Testing

The following elements will be validated:

- Status code
- Response body
- JSON structure
- Required fields
- Data types
- Response headers
- Content-Type

---

## 7.5 Exploratory Testing

Exploratory testing may be performed to identify unexpected API behavior that is not covered by predefined test cases.

Areas may include:

- Unexpected input combinations
- Boundary values
- Missing parameters
- Unexpected request data
- Response inconsistencies

---

## 7.6 Retesting

Previously identified defects will be retested after a correction or change has been made.

---

## 7.7 Regression Testing

Previously tested functionality may be re-executed after API changes to verify that existing behavior has not been negatively affected.

---

## 8. Testing Techniques

The following test design techniques will be applied where appropriate:

Equivalence Partitioning

Input data will be divided into representative valid and invalid classes.

### Boundary Value Analysis

Values around relevant boundaries will be tested when applicable.

### Positive Testing

Valid data will be used to verify normal behavior.

### Negative Testing

Invalid data and unexpected conditions will be used to verify error handling.

### Exploratory Testing

Additional behaviors and risks will be explored beyond predefined test cases.

---

## 9. Test Environment

Testing will be performed using:

Component| Configuration
API| ReqRes
Environment| QA
API Client| Postman
Automation| Newman
Data Format| JSON
Version Control| GitHub
Operating Environment| Local QA environment

The Postman environment will contain variables such as:

base_url
api_key
user_id
created_user_id
token
environment

Sensitive values will not be committed to the public repository.

---

## 10. Test Data

Test data will include:

### Authentication Data

- Valid credentials
- Invalid credentials
- Missing credentials
- Invalid email
- Missing password

### User Data

- Valid user information
- Missing fields
- Empty values
- Updated user information
- Partial update information

### User IDs

- Existing user IDs
- Non-existing user IDs
- Invalid user IDs

### API Authentication

- Valid API key
- Missing API key
- Invalid API key

---

## 11. Entry Criteria

Testing can begin when the following conditions are met:

- API documentation is available
- API endpoints are identified
- Test scope is defined
- Postman is available
- QA environment is configured
- Required API credentials are available
- Initial test data is prepared
- Postman collection structure is available

---

## 12. Exit Criteria

Testing can be considered complete when:

- Planned test cases have been executed
- Test results have been recorded
- Failed tests have been investigated
- Identified defects have been documented
- Critical test scenarios have been executed
- Newman execution has been completed
- Test reports have been generated
- Evidence has been collected
- Test summary has been prepared

The exit criteria may be adjusted depending on the actual test results and project findings.

---

## 13. Test Deliverables

The following deliverables will be produced:

01-API-Analysis/
02-Test-Plan/
03-Test-Scenarios/
04-Test-Cases/
05-Test-Data/
06-Postman/
07-Test-Execution/
08-Bug-Reports/
09-Reports/
10-Evidence/
11-Test-Summary/

Expected deliverables include:

- API documentation analysis
- Endpoint matrix
- Risk analysis
- Test Plan
- Test Scenarios
- Test Cases
- Test Data
- Postman Collection
- Postman Environment
- Test Execution results
- Bug Reports
- Newman Report
- Evidence
- Test Summary

---

## 14. Defect Management

Defects identified during testing will be documented using a structured bug report.

Each defect may include:

- Bug ID
- Summary
- Endpoint
- Preconditions
- Steps to Reproduce
- Expected Result
- Actual Result
- Severity
- Priority
- Environment
- Evidence
- Status

Defects will be classified according to their impact and urgency.

---

## 15. Severity Levels

Level| Description
High| Failure could significantly affect a critical function
Medium| Failure could affect functionality or user experience
Low| Failure has limited functional impact

---

## 16. Test Execution Status

The following statuses will be used:

Status| Description
PASS| Actual result matches the expected result
FAIL| Actual result does not match the expected result
BLOCKED| Test cannot be executed because of a blocking issue
NOT RUN| Test has not yet been executed

---

## 17. Automation Strategy

Postman will be used to create automated assertions for API responses.

Examples of automated validations include:

- HTTP status code
- Response body
- JSON properties
- Data values
- Data types
- Response headers
- Response time

The Postman Collection Runner will be used for collection-level execution.

Newman will be used to execute the collection from the command line and generate reports.

---

## 18. Traceability

Traceability will be maintained throughout the testing process.
```text 
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

Each test case will have a unique identifier.
```

Example:

```text 
Requirement: REQ-001
       ↓
Scenario: API-SC-001
       ↓
Test Case: TC-AUTH-001
       ↓
Postman Request
       ↓
Execution Result
       ↓
BUG-API-001
```

---

## 19. Risks

The main identified testing risks include:

- Authentication failures
- Incorrect API key handling
- Incorrect CRUD behavior
- Invalid data being accepted
- Incorrect HTTP status codes
- Incorrect response structures
- Missing response fields
- Unexpected API behavior
- Insufficient test coverage
- Exposure of sensitive API credentials

High-risk areas will receive additional testing attention.

---

## 20. Assumptions

The following assumptions apply to this project:

- The API is accessible during testing.
- The API documentation is available.
- Required API credentials are available.
- Test execution is performed against the intended API environment.
- The API is a public demonstration service and may change independently of this portfolio project.
- Test results will be based on actual observed API behavior.

---

## 21. Constraints

The project has the following constraints:

- The API is a public demonstration API.
- API behavior may change over time.
- No control is available over the backend implementation.
- No access to production infrastructure is available.
- No database access is included.
- No dedicated performance environment is available.

---

## 22. Reporting

Test execution results will be documented in:

### 07-Test-Execution/

Newman reports will be stored in:

### 09-Reports/

Evidence such as screenshots will be stored in:

### 10-Evidence/

The final testing conclusion will be documented in:

### 11-Test-Summary/

---

## 23. Roles and Responsibilities

| Role | Responsibility |
|---|---|
| QA Tester | Test analysis, test design, execution and reporting |
| QA Tester | Defect identification and documentation |
| QA Tester | Postman collection development |
| QA Tester | Newman execution |
| Development Team | Defect investigation and correction |
| Project Stakeholder | Review of test results and project status |

For this portfolio project, the QA activities are performed by the project author.

---

## 24. Tools

### Postman

Used for:

- API requests
- Collection management
- Environment management
- Automated assertions
- Test execution

### Newman

Used for:

- Command-line execution
- Automated collection execution
- Test reporting

### GitHub

Used for:

- Version control
- QA documentation
- Test artifacts
- Evidence
- Portfolio presentation

---

## 25. Success Criteria

The project will be considered successful when it demonstrates the ability to:

- Analyze an API
- Identify testing scope
- Design API test scenarios
- Design API test cases
- Prepare test data
- Create Postman requests
- Implement automated assertions
- Execute positive and negative tests
- Identify and document defects
- Execute a collection using Newman
- Generate test reports
- Maintain QA traceability
- Communicate test results clearly

---

## 26. Test Plan Status

Status: Approved for Test Design

The next phase is:

### 03-Test-Scenarios/
└── Test-Scenarios.md

The test scenarios will be derived from the API analysis, endpoint matrix, risks and scope defined in this Test Plan.
