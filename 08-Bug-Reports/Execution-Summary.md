# Execution Summary

## 1. Project Information

| Field | Details |
|---|---|
| Project | API Testing – User Management System |
| API Under Test | ReqRes |
| Base URL | https://reqres.in |
| Testing Tool | Postman |
| Environment | QA-API-Environment |
| Execution Date | 2026-09-18 |
| Test Cases Executed | 30 |
| Execution Status | Completed |

---

## 2. Execution Overview

The objective of this execution was to validate the functional behavior, authentication mechanisms, CRUD operations, input validation, response structure, and basic response quality of the ReqRes User Management API.

A total of 30 test cases were executed through Postman.

After execution and revalidation of tests initially affected by test configuration issues, the final result was:

- 28 PASS
- 2 FAIL
- 0 NOT RUN

### Final Execution Result

| Status | Count | Percentage |
|---|---:|---:|
| PASS | 28 | 93.3% |
| FAIL | 2 | 6.7% |
| NOT RUN | 0 | 0% |
| TOTAL | 30 | 100% |

---

## 3. Test Execution by Functional Area

| Functional Area | Test Cases | PASS | FAIL | Result |
|---|---:|---:|---:|---|
| Authentication | 5 | 4 | 1 | Partially Passed |
| API Authentication | 2 | 1 | 1 | Partially Passed |
| Users - GET | 7 | 7 | 0 | Passed |
| Users - POST | 5 | 5 | 0 | Passed |
| Users - PUT | 3 | 3 | 0 | Passed |
| Users - PATCH | 1 | 1 | 0 | Passed |
| Users - DELETE | 2 | 2 | 0 | Passed |
| Response Validation | 5 | 5 | 0 | Passed |
| TOTAL | 30 | 28 | 2 | 93.3% PASS |

---

## 4. Failed Test Cases

Two test cases failed during the final execution.

### TC-AUTH-002 — Login with invalid credentials

Scenario: API-SC-002

Result: FAIL

Observed behavior:

The login request was sent with an intentionally incorrect password.

The API returned:

text
HTTP 200 OK

or another appropriate authentication error.
Jira Defect:
- BUG-API-002
- Jira: SCRUM-27
- Status: Open
- Severity: High
- Priority: P1
The complete defect is documented in:
### 08-Bug-Reports/Bug-Reports.md

---

## 5. Defect Traceability

The failed test cases have been linked to their corresponding defect reports and Jira tickets.

| Test Scenario | Test Case | Bug Report | Jira | Status |
|---|---|---|---|---|
| API-SC-002 | TC-AUTH-002 | BUG-API-001 | SCRUM-26 | Open |
| API-SC-007 | TC-AUTH-006 | BUG-API-002 | SCRUM-27 | Open |

### Traceability Flow

```text
Requirement
    ↓
Test Scenario
    ↓
Test Case
    ↓
Test Execution
    ↓
Bug Report
    ↓
Jira
```

---

## 6. Revalidation Activities
During the initial execution, several test cases appeared as failed because of test configuration issues rather than API behavior.
The following issues were identified and corrected:
URL Variable Configuration
Several requests initially contained an incorrect {{user_id}} variable reference.
This caused requests to be sent with an incorrect URL representation.
```text 
The URLs were corrected to:
text 
{{base_url}}/api/users/{{user_id}}
```
The affected tests were then re-executed.
Variable Scope
TC-GET-003 initially had an assertion using the environment variable scope instead of the active Postman variable scope.

```text
The assertion was corrected to use:
text
pm.variables.get("user_id")
```
The test was then revalidated successfully.

- TC-AUTH-002
- TC-AUTH-006
  
---

## 7. Additional Observations

### POST Negative Test Cases

The following negative test cases returned HTTP 201 Created:

- TC-POST-002 — Create user with missing name
- TC-POST-003 — Create user with missing job
- TC-POST-004 — Create user with empty request body

These tests were retained as PASS according to the current test oracle used in the Postman collection.

The observed behavior was recorded as an observation rather than being reported as a defect.

Further refinement of the expected behavior could be considered in a future test cycle.

### PUT with Non-existing User ID

TC-PUT-002 returned:

```text
HTTP 200 OK
```
when using a non-existing user ID.
The current test oracle accepts the observed response, so the test remains PASS.
This behavior is recorded as an observation rather than a defect.

### Invalid API Key

TC-AUTH-007 was successfully revalidated.
The API returned:
```text
HTTP 403 Forbidden
```
with an invalid_api_key error response.
The test therefore passed successfully. 


---


## 8. Response Quality

The response validation tests were successfully executed.

The following aspects were validated:

- HTTP status code
- JSON Content-Type
- Response time
- JSON data types
- Required response fields
- User response structure
- Pagination metadata

All response validation test cases passed.

This confirms that the tested responses met the validation criteria defined in the test cases.

---

## 9. Execution Metrics

### Overall Metrics

| Metric | Value |
|---|---:|
| Total Test Cases | 30 |
| Executed | 30 |
| PASS | 28 |
| FAIL | 2 |
| NOT RUN | 0 |
| Pass Rate | 93.3% |
| Fail Rate | 6.7% |
| Execution Coverage | 100% |

### Defect Metrics

| Metric | Value |
|---|---:|
| Total Defects | 2 |
| Open Defects | 2 |
| Closed Defects | 0 |
| High Severity | 2 |
| P1 Priority | 2 | 

---

## 10. Evidence

Execution evidence was collected during the Postman test execution.

Evidence includes:

- Request configuration
- Request headers
- Request body
- HTTP status codes
- Response bodies
- Postman Test Results
- Failed assertions
- Revalidation results
- Jira defect references

Evidence related to individual defects is associated with:

- SCRUM-26
- SCRUM-27

Additional execution evidence can be stored in:

```text
10-Evidence/
```
---

## 11. Security Considerations

Authentication behavior was specifically tested because incorrect authentication handling can create security risks.

The execution identified two authentication-related discrepancies:

- Invalid credentials resulted in HTTP 200 and a token.
- A request without an API key resulted in HTTP 200 and user data.

Both issues were reported in Jira for investigation.

API keys and authentication tokens used during testing must not be committed to the GitHub repository.

Sensitive values should remain stored in the local Postman environment or another secure secret-management mechanism.

## 12. Overall Execution Conclusion

The final execution covered all 30 planned test cases, resulting in 28 passed tests and 2 failed tests.

The majority of the tested API functionality behaved according to the defined test oracle, including:

- User retrieval
- Pagination
- User creation
- User update
- Partial update
- User deletion
- Response structure validation
- Response data validation
- Invalid API key handling

Two authentication-related discrepancies remain open and have been reported in Jira:

- SCRUM-26 — Invalid credentials return HTTP 200 and a token
- SCRUM-27 — Request without API key returns HTTP 200

The test execution is therefore considered completed with open defects requiring investigation and follow-up.

## 13. Next Steps

The next activities in the project are:

- Review the two Jira defects and monitor their status.
- Generate the automated Newman HTML report from the Postman collection.
- Store relevant execution evidence in `10-Evidence/`.
- Prepare the final `11-Test-Summary/Test-Summary.md`.
- Review the complete project for portfolio presentation.
- Ensure that no API keys, tokens, or other sensitive information are committed to GitHub.

## 14. Project Traceability

The complete QA workflow demonstrated by this project is:

```text
API Documentation
        ↓
API Analysis
        ↓
Risk Analysis
        ↓
Test Plan
        ↓
Test Scenarios
        ↓
Test Cases
        ↓
Test Data
        ↓
Postman Collection
        ↓
Test Execution
        ↓
Bug Reporting
        ↓
Jira
        ↓
Newman Report
        ↓
Test Summary
```

This provides end-to-end traceability between the API analysis, test design, execution results, identified defects, and final QA reporting.
