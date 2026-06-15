# UAT Test Cases

## Project Name

Digital Mortgage Loan Origination & Applicant Tracking System

## Document Type

User Acceptance Testing Test Cases

## Domain

Banking / Mortgage / Financial Services

---

## 1. Purpose

This document contains User Acceptance Testing test cases for the Mortgage Loan Origination System enhancement.

The purpose of UAT is to validate that the system meets business requirements and supports real business workflows for borrowers, loan officers, underwriters, compliance users, and operations managers.

As a Business Analyst, this document supports business validation, UAT execution, defect discussion, requirement traceability, and final business sign-off.

---

## 2. UAT Scope

The following business areas are covered in UAT:

* Borrower registration and login
* Mortgage loan application submission
* Document upload
* Loan officer review
* Missing document request
* Underwriter review
* Approval, rejection, and additional information request
* Borrower status tracking
* Email notifications
* Operations manager dashboard
* Audit trail
* Search and filter

---

## 3. UAT Test Case Format

| Field           | Description                       |
| --------------- | --------------------------------- |
| Test Case ID    | Unique UAT test case number       |
| Requirement ID  | Related business requirement      |
| User Role       | Business user performing the test |
| Scenario        | Business scenario being validated |
| Precondition    | Required setup before testing     |
| Test Steps      | Step-by-step actions              |
| Expected Result | Expected business outcome         |
| Status          | Pass / Fail / Not Run             |
| Comments        | Additional notes                  |

---

## 4. UAT Test Cases

### TC-001: Verify Borrower Registration

| Field          | Details                                              |
| -------------- | ---------------------------------------------------- |
| Test Case ID   | TC-001                                               |
| Requirement ID | BR-001                                               |
| User Role      | Borrower                                             |
| Scenario       | Verify that a new borrower can register successfully |
| Precondition   | Borrower is not already registered                   |
| Status         | Not Run                                              |

**Test Steps**

1. Open borrower registration page.
2. Enter full name.
3. Enter valid email address.
4. Enter valid 10-digit phone number.
5. Enter password and confirm password.
6. Click Register.

**Expected Result**

* Borrower account should be created successfully.
* Borrower ID should be generated.
* Confirmation message should be displayed.
* Confirmation email should be sent to borrower.

---

### TC-002: Verify Borrower Login

| Field          | Details                                                 |
| -------------- | ------------------------------------------------------- |
| Test Case ID   | TC-002                                                  |
| Requirement ID | BR-001                                                  |
| User Role      | Borrower                                                |
| Scenario       | Verify that registered borrower can log in successfully |
| Precondition   | Borrower is already registered                          |
| Status         | Not Run                                                 |

**Test Steps**

1. Open borrower login page.
2. Enter registered email address.
3. Enter valid password.
4. Click Login.

**Expected Result**

* Borrower should be logged in successfully.
* Borrower dashboard should be displayed.
* Borrower should see their loan applications or option to create new application.

---

### TC-003: Verify Invalid Borrower Login

| Field          | Details                                    |
| -------------- | ------------------------------------------ |
| Test Case ID   | TC-003                                     |
| Requirement ID | BR-001                                     |
| User Role      | Borrower                                   |
| Scenario       | Verify login error for invalid credentials |
| Precondition   | Borrower login page is available           |
| Status         | Not Run                                    |

**Test Steps**

1. Open borrower login page.
2. Enter invalid email or password.
3. Click Login.

**Expected Result**

* System should display invalid credentials message.
* Borrower should not be logged in.
* Dashboard should not be accessible.

---

### TC-004: Verify Mortgage Loan Application Submission

| Field          | Details                                                   |
| -------------- | --------------------------------------------------------- |
| Test Case ID   | TC-004                                                    |
| Requirement ID | BR-002, BR-003, BR-005, BR-006                            |
| User Role      | Borrower                                                  |
| Scenario       | Verify that borrower can submit mortgage loan application |
| Precondition   | Borrower is registered and logged in                      |
| Status         | Not Run                                                   |

**Test Steps**

1. Login as borrower.
2. Click New Loan Application.
3. Enter personal details.
4. Enter employment details.
5. Enter income details.
6. Enter property details.
7. Enter loan details.
8. Submit application.

**Expected Result**

* Application should be submitted successfully.
* Unique application ID should be generated.
* Application status should be Submitted.
* Borrower should see application in dashboard.

---

### TC-005: Verify Mandatory Field Validation

| Field          | Details                                                         |
| -------------- | --------------------------------------------------------------- |
| Test Case ID   | TC-005                                                          |
| Requirement ID | BR-005                                                          |
| User Role      | Borrower                                                        |
| Scenario       | Verify mandatory field validation during application submission |
| Precondition   | Borrower is logged in                                           |
| Status         | Not Run                                                         |

**Test Steps**

1. Start new mortgage application.
2. Leave mandatory fields blank.
3. Click Submit Application.

**Expected Result**

* System should prevent submission.
* Validation messages should display for missing mandatory fields.
* Application should remain in Draft status.

---

### TC-006: Verify Save Application as Draft

| Field          | Details                                                  |
| -------------- | -------------------------------------------------------- |
| Test Case ID   | TC-006                                                   |
| Requirement ID | BR-002                                                   |
| User Role      | Borrower                                                 |
| Scenario       | Verify borrower can save incomplete application as draft |
| Precondition   | Borrower is logged in                                    |
| Status         | Not Run                                                  |

**Test Steps**

1. Start new mortgage application.
2. Enter partial application details.
3. Click Save as Draft.
4. Return to borrower dashboard.

**Expected Result**

* Application should be saved in Draft status.
* Borrower should be able to continue draft later.
* Draft application should be editable.

---

### TC-007: Verify Document Upload

| Field          | Details                                            |
| -------------- | -------------------------------------------------- |
| Test Case ID   | TC-007                                             |
| Requirement ID | BR-004                                             |
| User Role      | Borrower                                           |
| Scenario       | Verify borrower can upload required documents      |
| Precondition   | Borrower has submitted or drafted loan application |
| Status         | Not Run                                            |

**Test Steps**

1. Open document upload page.
2. Select document type as Pay Stub.
3. Upload valid PDF file.
4. Click Upload.
5. Repeat for W2, bank statement, tax return, and ID proof.

**Expected Result**

* Documents should upload successfully.
* Upload status should display as Submitted.
* Uploaded documents should be visible for loan officer review.

---

### TC-008: Verify Unsupported Document Format

| Field          | Details                                           |
| -------------- | ------------------------------------------------- |
| Test Case ID   | TC-008                                            |
| Requirement ID | BR-004                                            |
| User Role      | Borrower                                          |
| Scenario       | Verify system rejects unsupported document format |
| Precondition   | Borrower is on document upload page               |
| Status         | Not Run                                           |

**Test Steps**

1. Select document type.
2. Upload unsupported file type such as .exe or .txt.
3. Click Upload.

**Expected Result**

* System should reject the file.
* Error message should display unsupported file format.
* Document should not be uploaded.

---

### TC-009: Verify Document File Size Validation

| Field          | Details                                                  |
| -------------- | -------------------------------------------------------- |
| Test Case ID   | TC-009                                                   |
| Requirement ID | BR-004                                                   |
| User Role      | Borrower                                                 |
| Scenario       | Verify system rejects document greater than allowed size |
| Precondition   | Borrower is on document upload page                      |
| Status         | Not Run                                                  |

**Test Steps**

1. Select document type.
2. Upload file greater than 10 MB.
3. Click Upload.

**Expected Result**

* System should reject the file.
* Error message should display file size limit.
* Document should not be uploaded.

---

### TC-010: Verify Loan Officer Can View Submitted Applications

| Field          | Details                                             |
| -------------- | --------------------------------------------------- |
| Test Case ID   | TC-010                                              |
| Requirement ID | BR-007                                              |
| User Role      | Loan Officer                                        |
| Scenario       | Verify loan officer can view submitted applications |
| Precondition   | At least one borrower application is submitted      |
| Status         | Not Run                                             |

**Test Steps**

1. Login as loan officer.
2. Open loan officer dashboard.
3. View submitted applications queue.
4. Open one application.

**Expected Result**

* Loan officer should see submitted applications.
* Loan officer should view borrower details, loan details, and uploaded documents.
* Loan officer should be able to add review comments.

---

### TC-011: Verify Loan Officer Requests Missing Documents

| Field          | Details                                                         |
| -------------- | --------------------------------------------------------------- |
| Test Case ID   | TC-011                                                          |
| Requirement ID | BR-008                                                          |
| User Role      | Loan Officer                                                    |
| Scenario       | Verify loan officer can request missing documents from borrower |
| Precondition   | Submitted application has missing documents                     |
| Status         | Not Run                                                         |

**Test Steps**

1. Login as loan officer.
2. Open submitted application.
3. Select missing document type.
4. Add comments.
5. Click Request Missing Documents.

**Expected Result**

* Application status should update to Pending Documents.
* Borrower should receive notification.
* Action should be captured in audit trail.

---

### TC-012: Verify Loan Officer Moves Application to Underwriting

| Field          | Details                                                           |
| -------------- | ----------------------------------------------------------------- |
| Test Case ID   | TC-012                                                            |
| Requirement ID | BR-008                                                            |
| User Role      | Loan Officer                                                      |
| Scenario       | Verify loan officer can move complete application to underwriting |
| Precondition   | Application has all required documents                            |
| Status         | Not Run                                                           |

**Test Steps**

1. Login as loan officer.
2. Open complete submitted application.
3. Review details and documents.
4. Click Move to Underwriting.

**Expected Result**

* Application status should update to Underwriting.
* Application should appear in underwriter queue.
* Borrower should receive status notification.
* Status update should be captured in audit trail.

---

### TC-013: Verify Underwriter Can Review Application

| Field          | Details                                           |
| -------------- | ------------------------------------------------- |
| Test Case ID   | TC-013                                            |
| Requirement ID | BR-009                                            |
| User Role      | Underwriter                                       |
| Scenario       | Verify underwriter can review application details |
| Precondition   | Application is in Underwriting status             |
| Status         | Not Run                                           |

**Test Steps**

1. Login as underwriter.
2. Open underwriting queue.
3. Select application.
4. Review borrower details, income, property, loan details, and documents.

**Expected Result**

* Underwriter should be able to view complete application details.
* Underwriter should be able to add review comments.
* Review activity should be captured in audit trail.

---

### TC-014: Verify Underwriter Approves Application

| Field          | Details                                         |
| -------------- | ----------------------------------------------- |
| Test Case ID   | TC-014                                          |
| Requirement ID | BR-009                                          |
| User Role      | Underwriter                                     |
| Scenario       | Verify underwriter can approve loan application |
| Precondition   | Application is in Underwriting status           |
| Status         | Not Run                                         |

**Test Steps**

1. Login as underwriter.
2. Open application in underwriting queue.
3. Review details.
4. Select Approve.
5. Add approval comments.
6. Submit decision.

**Expected Result**

* Application status should update to Approved.
* Borrower should receive approval notification.
* Dashboard approved count should update.
* Approval should be captured in audit trail.

---

### TC-015: Verify Underwriter Rejects Application

| Field          | Details                                        |
| -------------- | ---------------------------------------------- |
| Test Case ID   | TC-015                                         |
| Requirement ID | BR-009                                         |
| User Role      | Underwriter                                    |
| Scenario       | Verify underwriter can reject loan application |
| Precondition   | Application is in Underwriting status          |
| Status         | Not Run                                        |

**Test Steps**

1. Login as underwriter.
2. Open application in underwriting queue.
3. Select Reject.
4. Enter rejection comments.
5. Submit decision.

**Expected Result**

* Application status should update to Rejected.
* Borrower should receive rejection notification.
* Rejected count should update in dashboard.
* Rejection comments should be captured in audit trail.

---

### TC-016: Verify Rejection Comments Are Mandatory

| Field          | Details                                               |
| -------------- | ----------------------------------------------------- |
| Test Case ID   | TC-016                                                |
| Requirement ID | BR-009                                                |
| User Role      | Underwriter                                           |
| Scenario       | Verify rejection cannot be submitted without comments |
| Precondition   | Application is in Underwriting status                 |
| Status         | Not Run                                               |

**Test Steps**

1. Login as underwriter.
2. Open application.
3. Select Reject.
4. Leave comments blank.
5. Click Submit Decision.

**Expected Result**

* System should prevent rejection.
* Mandatory comments validation message should display.
* Application status should remain Underwriting.

---

### TC-017: Verify Underwriter Requests Additional Information

| Field          | Details                                               |
| -------------- | ----------------------------------------------------- |
| Test Case ID   | TC-017                                                |
| Requirement ID | BR-009                                                |
| User Role      | Underwriter                                           |
| Scenario       | Verify underwriter can request additional information |
| Precondition   | Application is in Underwriting status                 |
| Status         | Not Run                                               |

**Test Steps**

1. Login as underwriter.
2. Open application.
3. Select Request Additional Information.
4. Add comments.
5. Submit request.

**Expected Result**

* Application status should update to Additional Info Required.
* Borrower should receive notification.
* Action should be captured in audit trail.

---

### TC-018: Verify Borrower Can Track Application Status

| Field          | Details                                     |
| -------------- | ------------------------------------------- |
| Test Case ID   | TC-018                                      |
| Requirement ID | BR-010                                      |
| User Role      | Borrower                                    |
| Scenario       | Verify borrower can view application status |
| Precondition   | Borrower has submitted application          |
| Status         | Not Run                                     |

**Test Steps**

1. Login as borrower.
2. Open borrower dashboard.
3. Select submitted application.
4. View current application status.

**Expected Result**

* Borrower should see application ID, submitted date, and current status.
* Borrower should not see internal-only comments.
* Status should match latest internal status.

---

### TC-019: Verify Email Notification for Status Change

| Field          | Details                                                        |
| -------------- | -------------------------------------------------------------- |
| Test Case ID   | TC-019                                                         |
| Requirement ID | BR-011                                                         |
| User Role      | Borrower                                                       |
| Scenario       | Verify borrower receives email when application status changes |
| Precondition   | Application status has changed                                 |
| Status         | Not Run                                                        |

**Test Steps**

1. Trigger application status change.
2. Check borrower registered email inbox.
3. Verify notification content.

**Expected Result**

* Borrower should receive status change email.
* Email should include application ID and latest status.
* Notification record should be created in system.

---

### TC-020: Verify Operations Manager Dashboard

| Field          | Details                                         |
| -------------- | ----------------------------------------------- |
| Test Case ID   | TC-020                                          |
| Requirement ID | BR-013                                          |
| User Role      | Operations Manager                              |
| Scenario       | Verify manager can view loan pipeline dashboard |
| Precondition   | Applications exist in different statuses        |
| Status         | Not Run                                         |

**Test Steps**

1. Login as operations manager.
2. Open loan pipeline dashboard.
3. Review dashboard metrics.
4. Apply date range and status filters.

**Expected Result**

* Dashboard should display total applications.
* Dashboard should display applications by status.
* Filters should update dashboard results.
* Dashboard values should match database/reporting data.

---

### TC-021: Verify Audit Trail

| Field          | Details                                                    |
| -------------- | ---------------------------------------------------------- |
| Test Case ID   | TC-021                                                     |
| Requirement ID | BR-012                                                     |
| User Role      | Compliance User                                            |
| Scenario       | Verify compliance user can view audit trail                |
| Precondition   | Application has status updates and document upload actions |
| Status         | Not Run                                                    |

**Test Steps**

1. Login as compliance user.
2. Open audit trail page.
3. Search by application ID.
4. Review audit records.

**Expected Result**

* Audit trail should display user ID, role, action type, old value, new value, timestamp, and comments.
* Audit records should be read-only.
* Compliance user should not be able to edit records.

---

### TC-022: Verify Search Application by Application ID

| Field          | Details                                                       |
| -------------- | ------------------------------------------------------------- |
| Test Case ID   | TC-022                                                        |
| Requirement ID | BR-014                                                        |
| User Role      | Internal User                                                 |
| Scenario       | Verify internal user can search application by application ID |
| Precondition   | Application exists in system                                  |
| Status         | Not Run                                                       |

**Test Steps**

1. Login as internal user.
2. Open application search page.
3. Enter valid application ID.
4. Click Search.

**Expected Result**

* Matching application should display.
* Search result should show application ID, borrower name, status, loan amount, and submitted date.

---

### TC-023: Verify Search Application by Status

| Field          | Details                                                |
| -------------- | ------------------------------------------------------ |
| Test Case ID   | TC-023                                                 |
| Requirement ID | BR-014                                                 |
| User Role      | Internal User                                          |
| Scenario       | Verify internal user can filter applications by status |
| Precondition   | Applications exist in multiple statuses                |
| Status         | Not Run                                                |

**Test Steps**

1. Login as internal user.
2. Open application search page.
3. Select status filter as Underwriting.
4. Click Search.

**Expected Result**

* Only applications in Underwriting status should display.
* Search results should match selected filter.

---

### TC-024: Verify Role-Based Access

| Field          | Details                                                                      |
| -------------- | ---------------------------------------------------------------------------- |
| Test Case ID   | TC-024                                                                       |
| Requirement ID | BR-015                                                                       |
| User Role      | Multiple Roles                                                               |
| Scenario       | Verify access is restricted based on user role                               |
| Precondition   | Users exist for borrower, loan officer, underwriter, manager, and compliance |
| Status         | Not Run                                                                      |

**Test Steps**

1. Login as borrower and verify borrower access.
2. Login as loan officer and verify review access.
3. Login as underwriter and verify decision access.
4. Login as manager and verify dashboard access.
5. Login as compliance user and verify audit access.

**Expected Result**

* Borrower should only access own applications.
* Loan officer should review applications but cannot approve/reject.
* Underwriter should approve/reject applications.
* Manager should view dashboard but not modify decisions.
* Compliance user should view audit trail only.

---

## 5. UAT Sign-Off Criteria

UAT can be considered complete when:

* All high-priority business scenarios are executed.
* Critical defects are resolved or accepted by business.
* Borrower application flow is validated end-to-end.
* Loan officer review workflow is validated.
* Underwriter decision workflow is validated.
* Dashboard and audit trail are validated.
* Business users provide sign-off.

---

## 6. BA Notes

As a Business Analyst, these UAT test cases help to:

* Validate business requirements before production release.
* Confirm that system behavior matches business expectations.
* Support UAT execution with business users.
* Track defects and requirement gaps.
* Support final business sign-off.
* Maintain traceability between BRD, FRD, user stories, and test scenarios.
