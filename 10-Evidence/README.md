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
