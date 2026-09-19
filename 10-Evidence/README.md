# Test Evidence

## 1. Purpose

This folder contains the evidence collected during the execution of the API tests for the **User Management System API**.

The purpose of the evidence is to provide visual and execution-based support for:

- Test execution results
- API request and response validation
- Authentication testing
- CRUD operations
- Response validation
- Defect investigation
- Newman automated execution

Evidence is linked to the corresponding Test Cases and Defects whenever applicable.

---

## 2. Evidence Types

The following types of evidence may be stored in this folder:

### Postman Evidence

Screenshots captured during manual or automated test execution in Postman.

Examples:

- Request configuration
- Request headers
- Request body
- HTTP status code
- Response body
- Test assertions
- Environment variables
- Failed test results

### Newman Evidence

Evidence generated from collection execution through Newman.

Examples:

- Newman CLI execution
- Test execution results
- Assertion failures
- Execution summary
- Newman HTML report

### Defect Evidence

Evidence supporting defects identified during testing.

Examples:

- Unexpected HTTP status codes
- Unexpected response body
- Authentication discrepancies
- Failed assertions
- Relevant Postman responses

---

## 3. Evidence Organization

Evidence is organized according to the main testing areas of the project.

```text
10-Evidence/
│
├── README.md
│
├── Authentication/
│   ├── TC-AUTH-001.png
│   ├── TC-AUTH-002.png
│   ├── TC-AUTH-006.png
│   └── TC-AUTH-007.png
│
├── Users/
│   ├── TC-GET-001.png
│   ├── TC-GET-003.png
│   ├── TC-GET-004.png
│   ├── TC-POST-001.png
│   ├── TC-PUT-001.png
│   ├── TC-PATCH-001.png
│   └── TC-DELETE-001.png
│
├── Validation/
│   ├── TC-VAL-001.png
│   ├── TC-VAL-002.png
│   ├── TC-VAL-004.png
│   └── TC-VAL-005.png
│
│
└── Defects/
    ├── BUG-API-001-SCRUM-26.png
    └── BUG-API-002-SCRUM-27.png
```
The exact evidence files may vary depending on the final execution and available screenshots.

---

## 4. Test Case → Evidence Traceability

Evidence should be directly associated with the relevant Test Case whenever possible.

```text 
| Test Case | Testing Area | Evidence |
|---|---|---|
| TC-AUTH-001 | Valid login | Postman request/response |
| TC-AUTH-002 | Invalid credentials | Postman response and failed assertion |
| TC-AUTH-003 | Missing password | Postman response |
| TC-AUTH-004 | Missing email | Postman response |
| TC-AUTH-006 | Missing API key | Postman response and failed assertion |
| TC-AUTH-007 | Invalid API key | Postman response |
| TC-GET-001 | Retrieve users | Postman response |
| TC-GET-003 | Retrieve user by ID | Postman request/response |
| TC-GET-004 | Non-existing user | Postman response |
| TC-POST-001 | Create user | Postman request/response |
| TC-PUT-001 | Update user | Postman request/response |
| TC-PATCH-001 | Partial update | Postman request/response |
| TC-DELETE-001 | Delete user | Postman response |
| TC-VAL-001 | HTTP status validation | Assertion result |
| TC-VAL-002 | Content-Type validation | Assertion result |
| TC-VAL-004 | JSON data types | Assertion result |
| TC-VAL-005 | Required fields | Assertion result |
```
---

## 5. Defect → Evidence Traceability

Evidence is also associated with reported defects.
```text 
| Defect | Test Case | Jira | Evidence Purpose |
|---|---|---|---|
| BUG-API-001 | TC-AUTH-002 | SCRUM-26 | Demonstrate invalid credentials returning an unexpected HTTP 200 response with a token |
| BUG-API-002 | TC-AUTH-006 | SCRUM-27 | Demonstrate a request without an API key returning HTTP 200 with user data |

```

The evidence should show the relevant request, response, and assertion result without exposing sensitive credentials or tokens.

---

## 6. Newman Evidence

Newman execution is documented through the generated execution report.

The Newman execution included:

- 30 requests
- 30 test scripts
- 80 assertions
- 16 failed assertions
- 19.6 seconds total execution time

The Newman report also documents:

- Failed assertions
- Authentication discrepancies
- Collection configuration issues
- Response-time observations
- Defect traceability

The Newman report represents the specific automated execution captured for this project.

---

## 7. Sensitive Data Handling

Sensitive information must not be committed to the repository.

The following information must be excluded or masked:

- API keys
- Authentication tokens
- Passwords
- Private credentials
- Personal or confidential data

Environment variables and secrets should be managed locally through the Postman environment.

Actual secret values must never be stored directly in the GitHub repository.

---

## 8. Evidence Quality Guidelines

Each screenshot or evidence file should:

- Clearly show the relevant test information
- Include the request or response context when necessary
- Show the HTTP status code when relevant
- Show the assertion result when relevant
- Avoid unnecessary personal or sensitive information
- Be readable at normal viewing size
- Be directly related to the corresponding Test Case or Defect

Evidence should support the test result rather than simply reproduce the entire Postman interface.

---

