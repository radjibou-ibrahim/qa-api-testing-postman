# Test Summary

## 1. Project Overview

**Project:** API Testing – User Management System  
**API:** ReqRes  
**Testing Tool:** Postman  
**Automation Tool:** Newman  
**Execution Date:** September 18, 2026

The objective of this project was to validate the functional behavior, authentication, CRUD operations, response validation, and selected quality aspects of the User Management API.

Detailed test documentation is available in the previous project sections.

---

## 2. Test Scope

The testing scope covered:

- Authentication
- API key validation
- User retrieval
- User creation
- User update
- Partial update
- User deletion
- Negative testing
- HTTP status validation
- Response structure validation
- JSON data type validation
- Required field validation
- Response-time observation

---

## 3. Test Execution Summary

### Manual Postman Revalidation

| Metric | Result |
|---|---:|
| Test Cases Executed | 30 |
| Passed | 28 |
| Failed | 2 |
| Not Run | 0 |

The two remaining functional failures were related to authentication:

- **TC-AUTH-002** — Invalid credentials
- **TC-AUTH-006** — Missing API key

These were documented as:

- **BUG-API-001 / SCRUM-26**
- **BUG-API-002 / SCRUM-27**

---

## 4. Newman Execution

The captured Newman execution produced:

| Metric | Result |
|---|---:|
| Requests | 30 |
| Test Scripts | 30 |
| Assertions | 80 |
| Failed Assertions | 16 |
| Request Failures | 0 |
| Total Duration | 19.6 s |
| Average Response Time | 540 ms |
| Maximum Response Time | 3.7 s |

The Newman results also revealed several collection configuration issues related to malformed `{{user_id}}` references.

These failures are therefore not all considered API defects.

Detailed results are documented in:

```text
09-Reports/Newman-Report.html
```
---

## 5. Configuration Issues
The Newman execution identified malformed user ID references in several requests:
```text 
/api/users/{{user_id}
```
These configuration issues affected several GET and response-validation tests and resulted in HTTP 404 responses.
They were classified as collection configuration issues, not API defects.

---

## 6. Performance Observation

One response-time assertion failed during the Newman execution:
- TC-AUTH-001
- Observed response time: 3728 ms
- Assertion threshold: 2000 ms
  
The overall average response time was 540 ms.
This observation should not be considered a complete performance assessment, as the project was primarily focused on functional API testing.

---

## 7. Evidence

Test evidence is maintained in:
```text 
10-Evidence/
```
Evidence provides traceability between:
```text 
Test Cases → Execution → Evidence → Defects
```
Sensitive information such as API keys and authentication tokens is excluded from the repository.

## 8. Traceability

The project maintains traceability across the main testing artifacts:
```text 
Requirements
     ↓
Test Scenarios
     ↓
Test Cases
     ↓
Test Execution
     ↓
Evidence
     ↓
Defects
     ↓
Test Summary

```
---

## 10. Risks and Limitations

The project used a public demo API and was not intended to represent a production-scale performance or security assessment.
The main limitations were:

- Public demo API environment
- Limited performance testing
- Limited security testing
- Differences observed between manual Postman and Newman execution
- Collection configuration issues requiring revalidation

## 11. Final Summary

The project demonstrated an end-to-end API testing workflow using Postman and Newman.
The testing covered functional scenarios, negative testing, authentication, CRUD operations, response validation, automated assertions, defect reporting, evidence collection, and automated execution.
The main findings were:

- Two authentication-related defects were identified and reported.
- Newman execution exposed additional collection configuration issues.
- A response-time observation was identified.
- The test suite can be further improved through collection correction and repeated Newman execution.

---

12. Next Steps
Correct the malformed {{user_id}} references.
- Re-run the Newman collection.
- Revalidate the affected test cases.
- Update the execution results.
- Update the final evidence where necessary.
- Review the final defect status.
- Maintain the project as a reusable API testing portfolio example. 
