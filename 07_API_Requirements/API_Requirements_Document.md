# API Requirements Document

## Project Name

Digital Mortgage Loan Origination & Applicant Tracking System

## Document Type

API Requirements Document

## Domain

Banking / Mortgage / Financial Services

---

## 1. Purpose

This document defines the API requirements for the Mortgage Loan Origination System enhancement.

The purpose of this document is to help business, development, QA, and integration teams understand API behavior, request fields, response fields, business rules, validation rules, and error scenarios.

As a Business Analyst, this document supports requirement clarification between frontend, backend, QA, product, and UAT teams.

---

## 2. API Scope

The following APIs are included in this project:

| API ID  | API Name                      | Method | Endpoint                                              |
| ------- | ----------------------------- | ------ | ----------------------------------------------------- |
| API-001 | Borrower Registration API     | POST   | /api/v1/borrowers/register                            |
| API-002 | Borrower Login API            | POST   | /api/v1/auth/login                                    |
| API-003 | Create Loan Application API   | POST   | /api/v1/loan-applications                             |
| API-004 | Get Loan Application API      | GET    | /api/v1/loan-applications/{applicationId}             |
| API-005 | Upload Document API           | POST   | /api/v1/loan-applications/{applicationId}/documents   |
| API-006 | Update Application Status API | PUT    | /api/v1/loan-applications/{applicationId}/status      |
| API-007 | Get Borrower Applications API | GET    | /api/v1/borrowers/{borrowerId}/applications           |
| API-008 | Get Loan Officer Queue API    | GET    | /api/v1/loan-officer/applications                     |
| API-009 | Get Underwriter Queue API     | GET    | /api/v1/underwriter/applications                      |
| API-010 | Get Manager Dashboard API     | GET    | /api/v1/dashboard/loan-pipeline                       |
| API-011 | Get Audit Trail API           | GET    | /api/v1/loan-applications/{applicationId}/audit-trail |

---

## 3. Common Header Requirements

| Header         | Required | Description                                              |
| -------------- | -------- | -------------------------------------------------------- |
| Authorization  | Yes      | Bearer token for secured APIs                            |
| Content-Type   | Yes      | application/json                                         |
| Correlation-ID | Yes      | Unique request tracking ID                               |
| Channel        | No       | Web, Mobile, Internal                                    |
| User-Role      | Yes      | Borrower, Loan Officer, Underwriter, Manager, Compliance |

---

## 4. Common Error Response Format

```json
{
  "errorCode": "ERR_400",
  "errorMessage": "Mandatory field is missing",
  "details": "loanAmount is required",
  "timestamp": "2026-06-15T10:00:00"
}
```

---

## 5. API-001: Borrower Registration API

### Method

POST

### Endpoint

```text
/api/v1/borrowers/register
```

### Purpose

Allows a new borrower to register in the mortgage portal.

### Request Body

```json
{
  "fullName": "John Smith",
  "email": "john.smith@email.com",
  "phoneNumber": "9876543210",
  "password": "Password@123"
}
```

### Response Body

```json
{
  "borrowerId": "BORR1001",
  "fullName": "John Smith",
  "email": "john.smith@email.com",
  "registrationStatus": "Success",
  "message": "Borrower registered successfully"
}
```

### Business Rules

* Email address must be unique.
* Phone number must contain 10 digits.
* Password must meet security requirements.
* Borrower profile should be created after successful registration.
* Confirmation email should be sent after successful registration.

### Error Scenarios

| Status Code | Scenario                                |
| ----------- | --------------------------------------- |
| 400         | Missing mandatory fields                |
| 409         | Email already exists                    |
| 422         | Invalid phone number or password format |
| 500         | Internal server error                   |

---

## 6. API-002: Borrower Login API

### Method

POST

### Endpoint

```text
/api/v1/auth/login
```

### Purpose

Authenticates borrower and returns an access token.

### Request Body

```json
{
  "email": "john.smith@email.com",
  "password": "Password@123"
}
```

### Response Body

```json
{
  "accessToken": "sample-jwt-token",
  "tokenType": "Bearer",
  "expiresIn": 3600,
  "userRole": "Borrower",
  "message": "Login successful"
}
```

### Business Rules

* Borrower must provide valid email and password.
* Token should expire after configured session time.
* Invalid login should not expose sensitive error details.
* Account should be locked after configured failed login attempts.

### Error Scenarios

| Status Code | Scenario                  |
| ----------- | ------------------------- |
| 400         | Missing email or password |
| 401         | Invalid credentials       |
| 423         | Account locked            |
| 500         | Internal server error     |

---

## 7. API-003: Create Loan Application API

### Method

POST

### Endpoint

```text
/api/v1/loan-applications
```

### Purpose

Creates a new mortgage loan application for a borrower.

### Request Body

```json
{
  "borrowerId": "BORR1001",
  "personalDetails": {
    "fullName": "John Smith",
    "dateOfBirth": "1990-05-15",
    "email": "john.smith@email.com",
    "phoneNumber": "9876543210",
    "ssnLastFour": "1234"
  },
  "employmentDetails": {
    "employerName": "ABC Technologies",
    "employmentType": "Full Time",
    "jobTitle": "Business Analyst",
    "yearsEmployed": 4
  },
  "incomeDetails": {
    "annualIncome": 95000,
    "monthlyIncome": 7916,
    "additionalIncome": 5000
  },
  "propertyDetails": {
    "propertyAddress": "123 Main Street, Dallas, TX",
    "propertyType": "Single Family",
    "purchasePrice": 450000,
    "occupancyType": "Primary Residence"
  },
  "loanDetails": {
    "loanAmount": 350000,
    "loanPurpose": "Home Purchase",
    "downPayment": 100000,
    "loanTerm": "30 Years"
  }
}
```

### Response Body

```json
{
  "applicationId": "LN100245",
  "borrowerId": "BORR1001",
  "status": "Submitted",
  "submittedDate": "2026-06-15",
  "message": "Loan application submitted successfully"
}
```

### Business Rules

* Borrower ID is mandatory.
* Loan amount must be greater than zero.
* Annual income must be greater than zero.
* SSN should contain only the last four digits.
* Application status should default to Submitted after final submission.
* Unique application ID should be generated after submission.
* Application submission should trigger confirmation email.

### Error Scenarios

| Status Code | Scenario                         |
| ----------- | -------------------------------- |
| 400         | Mandatory fields missing         |
| 401         | Unauthorized request             |
| 422         | Invalid business rule validation |
| 500         | Internal server error            |

---

## 8. API-004: Get Loan Application API

### Method

GET

### Endpoint

```text
/api/v1/loan-applications/{applicationId}
```

### Purpose

Retrieves loan application details using application ID.

### Sample Response

```json
{
  "applicationId": "LN100245",
  "borrowerId": "BORR1001",
  "borrowerName": "John Smith",
  "loanAmount": 350000,
  "loanPurpose": "Home Purchase",
  "status": "Underwriting",
  "submittedDate": "2026-06-15",
  "assignedLoanOfficer": "LO102",
  "assignedUnderwriter": "UW204",
  "documentStatus": "Complete"
}
```

### Business Rules

* Borrower can only view their own application.
* Loan officers can view applications assigned to their queue.
* Underwriters can view applications assigned to underwriting.
* Managers can view application summary details.
* Sensitive borrower data should be masked where applicable.

### Error Scenarios

| Status Code | Scenario              |
| ----------- | --------------------- |
| 401         | Unauthorized          |
| 403         | Forbidden access      |
| 404         | Application not found |
| 500         | Internal server error |

---

## 9. API-005: Upload Document API

### Method

POST

### Endpoint

```text
/api/v1/loan-applications/{applicationId}/documents
```

### Purpose

Allows borrower to upload required mortgage documents.

### Request Fields

| Field         | Type           | Required |
| ------------- | -------------- | -------- |
| applicationId | String         | Yes      |
| documentType  | String         | Yes      |
| fileName      | String         | Yes      |
| fileContent   | Multipart File | Yes      |

### Sample Response

```json
{
  "documentId": "DOC9001",
  "applicationId": "LN100245",
  "documentType": "Pay Stub",
  "fileName": "paystub_june.pdf",
  "uploadStatus": "Submitted",
  "uploadedDate": "2026-06-15"
}
```

### Business Rules

* Allowed file formats are PDF, JPG, and PNG.
* File size should not exceed 10 MB.
* Document upload should be captured in audit trail.
* Loan officer should be able to view uploaded documents.
* Borrower should be able to delete uploaded documents only before final submission.

### Error Scenarios

| Status Code | Scenario                      |
| ----------- | ----------------------------- |
| 400         | Missing document type or file |
| 401         | Unauthorized                  |
| 413         | File size exceeds limit       |
| 415         | Unsupported file type         |
| 500         | Internal server error         |

---

## 10. API-006: Update Application Status API

### Method

PUT

### Endpoint

```text
/api/v1/loan-applications/{applicationId}/status
```

### Purpose

Updates loan application status based on loan officer or underwriter action.

### Request Body

```json
{
  "applicationId": "LN100245",
  "currentStatus": "Underwriting",
  "newStatus": "Approved",
  "updatedBy": "UW204",
  "userRole": "Underwriter",
  "comments": "Application approved after income and document verification."
}
```

### Response Body

```json
{
  "applicationId": "LN100245",
  "oldStatus": "Underwriting",
  "newStatus": "Approved",
  "updatedBy": "UW204",
  "updatedDate": "2026-06-15T10:45:00",
  "message": "Application status updated successfully"
}
```

### Business Rules

* Loan officer can move applications to Underwriting but cannot approve or reject.
* Only underwriter can approve or reject application.
* Rejection comments are mandatory.
* Status change should trigger notification.
* Status change should be captured in audit trail.
* Invalid status transitions should not be allowed.

### Valid Status Transitions

| Current Status           | Allowed New Status       | Performed By |
| ------------------------ | ------------------------ | ------------ |
| Submitted                | In Review                | Loan Officer |
| In Review                | Pending Documents        | Loan Officer |
| Pending Documents        | Submitted                | Borrower     |
| In Review                | Underwriting             | Loan Officer |
| Underwriting             | Approved                 | Underwriter  |
| Underwriting             | Rejected                 | Underwriter  |
| Underwriting             | Additional Info Required | Underwriter  |
| Additional Info Required | Underwriting             | Borrower     |

### Error Scenarios

| Status Code | Scenario                                  |
| ----------- | ----------------------------------------- |
| 400         | Invalid status transition                 |
| 401         | Unauthorized                              |
| 403         | User not allowed to perform status update |
| 404         | Application not found                     |
| 422         | Missing required comments                 |
| 500         | Internal server error                     |

---

## 11. API-007: Get Borrower Applications API

### Method

GET

### Endpoint

```text
/api/v1/borrowers/{borrowerId}/applications
```

### Purpose

Displays all loan applications submitted by a borrower.

### Sample Response

```json
[
  {
    "applicationId": "LN100245",
    "loanAmount": 350000,
    "loanPurpose": "Home Purchase",
    "status": "Underwriting",
    "submittedDate": "2026-06-15",
    "actionRequired": false
  },
  {
    "applicationId": "LN100300",
    "loanAmount": 280000,
    "loanPurpose": "Refinance",
    "status": "Pending Documents",
    "submittedDate": "2026-06-18",
    "actionRequired": true
  }
]
```

### Business Rules

* Borrower should only see their own applications.
* Action required should display true when borrower must upload missing documents or provide additional information.
* Draft and submitted applications should both be shown in borrower dashboard.

### Error Scenarios

| Status Code | Scenario                                          |
| ----------- | ------------------------------------------------- |
| 401         | Unauthorized                                      |
| 403         | Borrower trying to access another borrower's data |
| 404         | Borrower applications not found                   |
| 500         | Internal server error                             |

---

## 12. API-008: Get Loan Officer Queue API

### Method

GET

### Endpoint

```text
/api/v1/loan-officer/applications
```

### Purpose

Displays applications assigned to the loan officer review queue.

### Sample Response

```json
[
  {
    "applicationId": "LN100245",
    "borrowerName": "John Smith",
    "loanAmount": 350000,
    "status": "Submitted",
    "documentStatus": "Complete",
    "submittedDate": "2026-06-15"
  },
  {
    "applicationId": "LN100300",
    "borrowerName": "Sarah Lee",
    "loanAmount": 280000,
    "status": "Pending Documents",
    "documentStatus": "Incomplete",
    "submittedDate": "2026-06-18"
  }
]
```

### Business Rules

* Loan officer should only see assigned or queue-eligible applications.
* Applications pending documents should be flagged.
* Loan officer can request missing documents.
* Loan officer can move complete applications to underwriting.

### Error Scenarios

| Status Code | Scenario                                         |
| ----------- | ------------------------------------------------ |
| 401         | Unauthorized                                     |
| 403         | User is not allowed to access loan officer queue |
| 500         | Internal server error                            |

---

## 13. API-009: Get Underwriter Queue API

### Method

GET

### Endpoint

```text
/api/v1/underwriter/applications
```

### Purpose

Displays applications ready for underwriting review.

### Sample Response

```json
[
  {
    "applicationId": "LN100245",
    "borrowerName": "John Smith",
    "loanAmount": 350000,
    "status": "Underwriting",
    "receivedDate": "2026-06-16",
    "assignedUnderwriter": "UW204"
  }
]
```

### Business Rules

* Only applications in Underwriting status should appear.
* Underwriter can open details and take decision.
* Underwriter can approve, reject, or request additional information.

### Error Scenarios

| Status Code | Scenario                                         |
| ----------- | ------------------------------------------------ |
| 401         | Unauthorized                                     |
| 403         | User is not allowed to access underwriting queue |
| 500         | Internal server error                            |

---

## 14. API-010: Get Manager Dashboard API

### Method

GET

### Endpoint

```text
/api/v1/dashboard/loan-pipeline
```

### Purpose

Displays loan pipeline summary for operations manager.

### Query Parameters

| Parameter     | Required | Example    |
| ------------- | -------- | ---------- |
| startDate     | No       | 2026-06-01 |
| endDate       | No       | 2026-06-30 |
| status        | No       | Approved   |
| loanOfficerId | No       | LO102      |
| underwriterId | No       | UW204      |

### Sample Response

```json
{
  "totalApplications": 250,
  "submitted": 60,
  "pendingDocuments": 35,
  "inReview": 40,
  "underwriting": 55,
  "approved": 45,
  "rejected": 15,
  "slaBreached": 12,
  "averageProcessingDays": 6
}
```

### Business Rules

* Dashboard should refresh based on latest application status.
* Manager can filter by date range and status.
* Dashboard data should match loan application database.
* Manager should be able to export dashboard summary to Excel.

### Error Scenarios

| Status Code | Scenario                                        |
| ----------- | ----------------------------------------------- |
| 401         | Unauthorized                                    |
| 403         | User is not allowed to access manager dashboard |
| 500         | Internal server error                           |

---

## 15. API-011: Get Audit Trail API

### Method

GET

### Endpoint

```text
/api/v1/loan-applications/{applicationId}/audit-trail
```

### Purpose

Displays audit history for a loan application.

### Sample Response

```json
[
  {
    "applicationId": "LN100245",
    "userId": "LO102",
    "userRole": "Loan Officer",
    "actionType": "STATUS_UPDATE",
    "oldValue": "Submitted",
    "newValue": "Underwriting",
    "timestamp": "2026-06-15T09:30:00",
    "comments": "Application complete and moved to underwriting."
  },
  {
    "applicationId": "LN100245",
    "userId": "UW204",
    "userRole": "Underwriter",
    "actionType": "DECISION",
    "oldValue": "Underwriting",
    "newValue": "Approved",
    "timestamp": "2026-06-15T10:45:00",
    "comments": "Approved after income verification."
  }
]
```

### Business Rules

* Audit records should be read-only.
* Audit trail should capture user ID, role, timestamp, old value, new value, and comments.
* Compliance users should have access to audit history.
* Audit records should not be editable.
* Audit should capture document upload, status update, comments, approval, rejection, and missing document requests.

### Error Scenarios

| Status Code | Scenario                                  |
| ----------- | ----------------------------------------- |
| 401         | Unauthorized                              |
| 403         | User is not allowed to access audit trail |
| 404         | Audit records not found                   |
| 500         | Internal server error                     |

---

## 16. Field-Level Validation Summary

| Field        | Validation Rule                                            |
| ------------ | ---------------------------------------------------------- |
| email        | Must be valid email format                                 |
| phoneNumber  | Must be 10 digits                                          |
| ssnLastFour  | Must be exactly 4 digits                                   |
| loanAmount   | Must be greater than zero                                  |
| annualIncome | Must be greater than zero                                  |
| documentType | Must be selected before upload                             |
| fileContent  | Must be PDF, JPG, or PNG                                   |
| comments     | Mandatory for rejection and additional information request |

---

## 17. BA Notes

As a Business Analyst, this API Requirements Document helps to:

* Clarify integration expectations between frontend and backend teams.
* Define request and response fields.
* Document business rules for API behavior.
* Support QA team with API test scenarios.
* Help developers understand validation and error handling.
* Support Postman and Swagger review discussions.
* Maintain traceability between business requirements and technical implementation.
* Support UAT teams in validating API-driven business workflows.

---

## 18. Approval

| Name             | Role           | Approval Status |
| ---------------- | -------------- | --------------- |
| Product Owner    | Business Owner | Pending         |
| Technical Lead   | API Owner      | Pending         |
| QA Lead          | Testing Owner  | Pending         |
| Business Analyst | Document Owner | Drafted         |
