# User Stories and Acceptance Criteria

## Project Name

Digital Mortgage Loan Origination & Applicant Tracking System

## Document Type

User Stories and Acceptance Criteria

## Domain

Banking / Mortgage / Financial Services

---

## Epic 1: Borrower Registration and Login

### US-001: Borrower Registration

**As a** borrower,  
**I want to** register using my personal details,  
**So that** I can access the mortgage loan application portal.

**Priority:** High  
**Sprint:** Sprint 1  
**Status:** Ready

#### Acceptance Criteria

1. Borrower should be able to enter full name, email, phone number, and password.
2. System should validate email format.
3. System should validate phone number as 10 digits.
4. Password should meet minimum security requirements.
5. System should create a borrower profile after successful registration.
6. Borrower should receive registration confirmation email.

---

### US-002: Borrower Login

**As a** borrower,  
**I want to** log in using my registered email and password,  
**So that** I can access my loan application dashboard.

**Priority:** High  
**Sprint:** Sprint 1  
**Status:** Ready

#### Acceptance Criteria

1. Borrower should be able to log in with valid credentials.
2. System should display an error message for invalid credentials.
3. Borrower should be redirected to dashboard after successful login.
4. System should not allow access without authentication.
5. Session should expire after inactivity.

---

## Epic 2: Mortgage Loan Application Submission

### US-003: Create New Loan Application

**As a** borrower,  
**I want to** create a new mortgage loan application,  
**So that** I can apply for a home loan online.

**Priority:** High  
**Sprint:** Sprint 1  
**Status:** Ready

#### Acceptance Criteria

1. Borrower should be able to start a new mortgage application.
2. System should create application in Draft status.
3. Borrower should be able to save the application before final submission.
4. System should generate an application ID after final submission.
5. Submitted application should be visible in borrower dashboard.

---

### US-004: Enter Personal Details

**As a** borrower,  
**I want to** enter my personal details,  
**So that** the lender can identify and verify my profile.

**Priority:** High  
**Sprint:** Sprint 1  
**Status:** Ready

#### Acceptance Criteria

1. Borrower should be able to enter full name, date of birth, email, phone number, and SSN last four digits.
2. Mandatory fields should be clearly marked.
3. System should validate email format.
4. System should validate phone number format.
5. SSN field should accept only four digits.
6. Borrower should not be able to submit if mandatory fields are missing.

---

### US-005: Enter Employment and Income Details

**As a** borrower,  
**I want to** enter my employment and income details,  
**So that** the lender can review my repayment capacity.

**Priority:** High  
**Sprint:** Sprint 1  
**Status:** Ready

#### Acceptance Criteria

1. Borrower should be able to enter employer name, employment type, job title, and years employed.
2. Borrower should be able to enter annual income and monthly income.
3. Annual income should be mandatory.
4. Income values should accept only numeric values.
5. System should display validation message for invalid income values.

---

### US-006: Enter Property and Loan Details

**As a** borrower,  
**I want to** enter property and loan details,  
**So that** the lender can evaluate the mortgage request.

**Priority:** High  
**Sprint:** Sprint 1  
**Status:** Ready

#### Acceptance Criteria

1. Borrower should be able to enter property address, property type, purchase price, and occupancy type.
2. Borrower should be able to enter loan amount, loan purpose, down payment, and loan term.
3. Loan amount should be greater than zero.
4. Purchase price should be greater than zero.
5. Required fields should be validated before moving to the next step.

---

## Epic 3: Document Upload

### US-007: Upload Required Documents

**As a** borrower,  
**I want to** upload required mortgage documents,  
**So that** my loan application can be reviewed by the loan officer and underwriter.

**Priority:** High  
**Sprint:** Sprint 1  
**Status:** Ready

#### Acceptance Criteria

1. Borrower should be able to upload documents such as pay stubs, W2, bank statements, tax returns, and ID proof.
2. System should allow PDF, JPG, and PNG file formats.
3. System should reject unsupported file types.
4. File size should not exceed 10 MB.
5. Uploaded documents should show status as Submitted.
6. Loan officer should be able to view uploaded documents.

---

### US-008: Delete Uploaded Document Before Submission

**As a** borrower,  
**I want to** delete an uploaded document before final submission,  
**So that** I can correct mistakes before submitting my application.

**Priority:** Medium  
**Sprint:** Sprint 1  
**Status:** Ready

#### Acceptance Criteria

1. Borrower should be able to delete documents before final application submission.
2. System should ask for confirmation before deleting.
3. Deleted document should no longer be visible in the upload list.
4. Borrower should be able to upload a replacement document.
5. Borrower should not be able to delete documents after application is submitted.

---

## Epic 4: Loan Officer Review

### US-009: View Submitted Applications

**As a** loan officer,  
**I want to** view submitted loan applications,  
**So that** I can review borrower details and application completeness.

**Priority:** High  
**Sprint:** Sprint 2  
**Status:** Ready

#### Acceptance Criteria

1. Loan officer should be able to view applications in Submitted and Pending Documents status.
2. Loan officer should be able to open application details.
3. Loan officer should be able to view borrower personal, employment, income, property, and loan details.
4. Loan officer should be able to view uploaded documents.
5. Loan officer should only see applications assigned to them or within their queue.

---

### US-010: Request Missing Documents

**As a** loan officer,  
**I want to** request missing documents from the borrower,  
**So that** the application can be completed before underwriting.

**Priority:** High  
**Sprint:** Sprint 2  
**Status:** Ready

#### Acceptance Criteria

1. Loan officer should be able to select missing document types.
2. Loan officer should be able to add comments for borrower.
3. System should update application status to Pending Documents.
4. Borrower should receive email notification.
5. Action should be captured in audit trail.

---

### US-011: Move Application to Underwriting

**As a** loan officer,  
**I want to** move a complete application to underwriting,  
**So that** the underwriter can review the loan request.

**Priority:** High  
**Sprint:** Sprint 2  
**Status:** Ready

#### Acceptance Criteria

1. Loan officer should be able to move application to underwriting only when required documents are uploaded.
2. System should update status to Underwriting.
3. Borrower should receive status update notification.
4. Underwriter queue should display the application.
5. Action should be captured in audit trail.

---

## Epic 5: Underwriter Decision Workflow

### US-012: Review Application as Underwriter

**As an** underwriter,  
**I want to** review borrower details, income details, property details, and uploaded documents,  
**So that** I can make a loan decision.

**Priority:** High  
**Sprint:** Sprint 2  
**Status:** Ready

#### Acceptance Criteria

1. Underwriter should be able to view applications in Underwriting status.
2. Underwriter should be able to open application details.
3. Underwriter should be able to view uploaded documents.
4. Underwriter should be able to add review comments.
5. System should capture underwriter review activity in audit trail.

---

### US-013: Approve Loan Application

**As an** underwriter,  
**I want to** approve a loan application,  
**So that** the borrower can move forward in the mortgage process.

**Priority:** High  
**Sprint:** Sprint 2  
**Status:** Ready

#### Acceptance Criteria

1. Underwriter should be able to approve application.
2. System should update application status to Approved.
3. Borrower should receive approval notification.
4. Operations manager dashboard should reflect approved count.
5. Approval action should be captured in audit trail.

---

### US-014: Reject Loan Application

**As an** underwriter,  
**I want to** reject a loan application with comments,  
**So that** the decision is clearly documented.

**Priority:** High  
**Sprint:** Sprint 2  
**Status:** Ready

#### Acceptance Criteria

1. Underwriter should be able to reject application.
2. Rejection comments should be mandatory.
3. System should update application status to Rejected.
4. Borrower should receive rejection notification.
5. Rejection action and comments should be captured in audit trail.

---

### US-015: Request Additional Information

**As an** underwriter,  
**I want to** request additional information from the borrower,  
**So that** I can complete the underwriting decision.

**Priority:** High  
**Sprint:** Sprint 2  
**Status:** Ready

#### Acceptance Criteria

1. Underwriter should be able to request additional documents or details.
2. Underwriter should be able to add comments.
3. System should update status to Additional Info Required.
4. Borrower should receive email notification.
5. Action should be captured in audit trail.

---

## Epic 6: Borrower Status Tracking

### US-016: View Application Status

**As a** borrower,  
**I want to** view my loan application status,  
**So that** I can track progress without contacting the loan officer.

**Priority:** High  
**Sprint:** Sprint 3  
**Status:** Ready

#### Acceptance Criteria

1. Borrower should be able to view all submitted applications.
2. Borrower should see current status for each application.
3. Borrower should see submitted date and application ID.
4. Borrower should not see internal-only comments.
5. Status should update based on loan officer or underwriter actions.

---

## Epic 7: Notifications

### US-017: Receive Status Change Notifications

**As a** borrower,  
**I want to** receive email notifications when my loan status changes,  
**So that** I stay informed about my application progress.

**Priority:** Medium  
**Sprint:** Sprint 3  
**Status:** Ready

#### Acceptance Criteria

1. Borrower should receive email when application is submitted.
2. Borrower should receive email when missing documents are requested.
3. Borrower should receive email when application moves to underwriting.
4. Borrower should receive email when application is approved or rejected.
5. Email should include application ID and latest status.

---

## Epic 8: Manager Dashboard and Reporting

### US-018: View Loan Pipeline Dashboard

**As an** operations manager,  
**I want to** view a loan pipeline dashboard,  
**So that** I can monitor application volume and processing status.

**Priority:** Medium  
**Sprint:** Sprint 3  
**Status:** Ready

#### Acceptance Criteria

1. Dashboard should display total applications submitted.
2. Dashboard should display applications by status.
3. Dashboard should display approved and rejected counts.
4. Dashboard should display applications pending documents.
5. Manager should be able to filter dashboard by date range.

---

### US-019: View Application Aging Report

**As an** operations manager,  
**I want to** view applications pending beyond SLA,  
**So that** I can identify delayed applications and take action.

**Priority:** Medium  
**Sprint:** Sprint 3  
**Status:** Ready

#### Acceptance Criteria

1. Report should display applications pending beyond defined SLA.
2. Report should show application ID, borrower name, status, assigned user, and pending days.
3. Manager should be able to filter by status and date range.
4. Report should be exportable to Excel.
5. Aging calculation should be based on submitted date and current date.

---

## Epic 9: Audit and Compliance

### US-020: View Audit Trail

**As a** compliance user,  
**I want to** view audit trail for loan applications,  
**So that** I can verify status changes and user actions.

**Priority:** High  
**Sprint:** Sprint 3  
**Status:** Ready

#### Acceptance Criteria

1. Compliance user should be able to search audit history by application ID.
2. Audit trail should show user ID, role, action, old status, new status, timestamp, and comments.
3. Compliance user should have read-only access.
4. Audit records should not be editable.
5. Audit trail should include document upload, status update, and decision actions.

---

## Epic 10: Search and Filter

### US-021: Search Loan Applications

**As an** internal user,  
**I want to** search loan applications by borrower name, application ID, status, and date range,  
**So that** I can quickly find the required application.

**Priority:** Medium  
**Sprint:** Sprint 3  
**Status:** Ready

#### Acceptance Criteria

1. Internal user should be able to search by application ID.
2. Internal user should be able to search by borrower name.
3. Internal user should be able to filter by status.
4. Internal user should be able to filter by date range.
5. Search results should display matching applications only.

---

## User Story Summary

| Epic | User Stories |
|---|---|
| Borrower Registration and Login | US-001 to US-002 |
| Mortgage Loan Application Submission | US-003 to US-006 |
| Document Upload | US-007 to US-008 |
| Loan Officer Review | US-009 to US-011 |
| Underwriter Decision Workflow | US-012 to US-015 |
| Borrower Status Tracking | US-016 |
| Notifications | US-017 |
| Manager Dashboard and Reporting | US-018 to US-019 |
| Audit and Compliance | US-020 |
| Search and Filter | US-021 |