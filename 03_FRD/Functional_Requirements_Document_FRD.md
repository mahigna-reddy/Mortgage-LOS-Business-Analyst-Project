# Functional Requirements Document

## Project Name

Digital Mortgage Loan Origination & Applicant Tracking System

## Document Type

Functional Requirements Document

## Domain

Banking / Mortgage / Financial Services


---

## 1. Purpose

This Functional Requirements Document defines the system behavior, user roles, workflows, validation rules, notifications, reporting needs, and audit requirements for the Mortgage Loan Origination System enhancement.

The purpose of this document is to translate business requirements into functional requirements that can be used by development, QA, product, and UAT teams.

---

## 2. Functional Scope

The system will support the following functional areas:

- Borrower registration and login
- Mortgage loan application submission
- Borrower document upload
- Loan officer application review
- Underwriter decision workflow
- Borrower application status tracking
- Automated email notifications
- Manager loan pipeline dashboard
- Audit trail for status changes
- Search and filter functionality
- Role-based access control

---

## 3. User Roles

| User Role | Description |
|---|---|
| Borrower | External user who submits loan application and uploads documents |
| Loan Officer | Internal user who reviews application completeness |
| Underwriter | Internal user who reviews loan risk and makes decision |
| Operations Manager | Internal user who monitors loan pipeline and dashboard |
| Compliance User | Internal user who reviews audit trail and compliance data |
| Admin | Internal user who manages system configuration and user access |

---

## 4. Functional Requirements

| Requirement ID | Functional Requirement | Priority |
|---|---|---|
| FR-001 | The system shall allow borrowers to register using name, email, phone number, and password. | High |
| FR-002 | The system shall allow borrowers to log in securely using valid credentials. | High |
| FR-003 | The system shall allow borrowers to create a new mortgage loan application. | High |
| FR-004 | The system shall capture borrower personal details including full name, DOB, SSN last four digits, email, and phone number. | High |
| FR-005 | The system shall capture employment details including employer name, employment type, job title, and years employed. | High |
| FR-006 | The system shall capture income details including annual income, monthly income, and additional income. | High |
| FR-007 | The system shall capture property details including property address, property type, purchase price, and occupancy type. | High |
| FR-008 | The system shall capture loan details including loan amount, loan purpose, down payment, and loan term. | High |
| FR-009 | The system shall allow borrowers to upload required documents. | High |
| FR-010 | The system shall validate required fields before application submission. | High |
| FR-011 | The system shall generate a unique application ID after successful submission. | High |
| FR-012 | The system shall display application status to the borrower. | High |
| FR-013 | The system shall allow loan officers to view submitted applications. | High |
| FR-014 | The system shall allow loan officers to add review comments. | High |
| FR-015 | The system shall allow loan officers to move complete applications to underwriting. | High |
| FR-016 | The system shall allow loan officers to request missing documents from borrowers. | High |
| FR-017 | The system shall allow underwriters to review application details and uploaded documents. | High |
| FR-018 | The system shall allow underwriters to approve applications. | High |
| FR-019 | The system shall allow underwriters to reject applications with mandatory comments. | High |
| FR-020 | The system shall allow underwriters to request additional documents. | High |
| FR-021 | The system shall send email notifications when application status changes. | Medium |
| FR-022 | The system shall maintain an audit trail for every status update. | High |
| FR-023 | The system shall provide dashboard metrics for operations managers. | Medium |
| FR-024 | The system shall allow internal users to search applications by borrower name, application ID, status, and date range. | Medium |
| FR-025 | The system shall restrict system access based on user role. | High |

---

## 5. Application Status Values

The system shall support the following loan application statuses:

| Status | Description |
|---|---|
| Draft | Borrower started the application but has not submitted it |
| Submitted | Borrower submitted the application |
| Pending Documents | Required documents are missing |
| In Review | Loan officer is reviewing the application |
| Underwriting | Application is under underwriter review |
| Additional Info Required | Underwriter requested more details or documents |
| Approved | Loan application is approved |
| Rejected | Loan application is rejected |
| Withdrawn | Borrower withdrew the application |

---

## 6. Validation Rules

| Rule ID | Validation Rule |
|---|---|
| VAL-001 | Email address must be in valid email format. |
| VAL-002 | Phone number must contain 10 digits. |
| VAL-003 | Loan amount must be greater than zero. |
| VAL-004 | Annual income must be greater than zero. |
| VAL-005 | Required fields cannot be blank. |
| VAL-006 | Uploaded document format must be PDF, JPG, or PNG. |
| VAL-007 | Uploaded document size must not exceed 10 MB. |
| VAL-008 | SSN field should capture only the last four digits. |
| VAL-009 | Rejection comments are mandatory for underwriter rejection. |
| VAL-010 | Application cannot move to underwriting until required documents are uploaded. |

---

## 7. Business Rules

| Rule ID | Business Rule |
|---|---|
| BUS-001 | Borrower can save application as draft before submission. |
| BUS-002 | Borrower can edit application only before final submission. |
| BUS-003 | Submitted applications cannot be deleted by borrower. |
| BUS-004 | Loan officer can review applications but cannot approve or reject loans. |
| BUS-005 | Only underwriters can approve or reject loan applications. |
| BUS-006 | Managers can view dashboard and reports but cannot update loan decisions. |
| BUS-007 | Compliance users can view audit trail but cannot modify application data. |
| BUS-008 | All status changes must be captured in audit history. |
| BUS-009 | Borrower must receive notification for every major status change. |
| BUS-010 | Applications pending documents should be flagged on loan officer dashboard. |

---

## 8. Notification Requirements

| Notification ID | Trigger | Recipient | Message Purpose |
|---|---|---|---|
| NOT-001 | Application submitted | Borrower | Confirm successful application submission |
| NOT-002 | Missing documents requested | Borrower | Notify borrower to upload missing documents |
| NOT-003 | Application moved to underwriting | Borrower | Inform borrower that application is under review |
| NOT-004 | Additional information requested | Borrower | Request additional details or documents |
| NOT-005 | Application approved | Borrower | Notify approval decision |
| NOT-006 | Application rejected | Borrower | Notify rejection decision |
| NOT-007 | Application pending review | Loan Officer | Alert internal user for review |
| NOT-008 | Underwriting decision completed | Operations Manager | Notify manager for reporting visibility |

---

## 9. Reporting Requirements

| Report ID | Report Name | Description |
|---|---|---|
| REP-001 | Loan Pipeline Dashboard | Shows total applications by status |
| REP-002 | Pending Documents Report | Shows applications waiting for borrower documents |
| REP-003 | Underwriting Queue Report | Shows applications currently in underwriting |
| REP-004 | Approved Loans Report | Shows approved applications by date range |
| REP-005 | Rejected Loans Report | Shows rejected applications with reason |
| REP-006 | Application Aging Report | Shows applications pending beyond expected SLA |
| REP-007 | Audit Trail Report | Shows status changes, users, timestamps, and comments |

---

## 10. Dashboard Metrics

The operations manager dashboard shall display:

- Total applications submitted
- Applications in draft
- Applications pending documents
- Applications in loan officer review
- Applications in underwriting
- Approved applications
- Rejected applications
- Average application processing time
- Applications pending beyond SLA
- Applications by submission date

---

## 11. Search and Filter Requirements

Internal users shall be able to search or filter loan applications by:

- Application ID
- Borrower name
- Borrower email
- Loan status
- Submission date
- Loan amount range
- Assigned loan officer
- Assigned underwriter
- Document status

---

## 12. Security Requirements

| Security ID | Requirement |
|---|---|
| SEC-001 | The system shall require login for all users. |
| SEC-002 | The system shall enforce role-based access control. |
| SEC-003 | Borrowers shall only view their own applications. |
| SEC-004 | Internal users shall access records based on assigned role. |
| SEC-005 | Sensitive borrower data shall be masked where applicable. |
| SEC-006 | SSN shall display only last four digits. |
| SEC-007 | User sessions shall expire after inactivity. |

---

## 13. Audit Requirements

The system shall capture audit history for:

- Application creation
- Application submission
- Document upload
- Document deletion
- Status update
- Loan officer comments
- Underwriter decision
- Missing document request
- Additional information request
- Approval or rejection decision

Audit trail should capture:

- Application ID
- User ID
- User role
- Action performed
- Old value
- New value
- Timestamp
- Comments

---

## 14. UAT Considerations

UAT will validate that:

- Borrowers can complete loan application submission.
- Borrowers can upload documents successfully.
- Loan officers can review applications.
- Underwriters can approve, reject, or request additional documents.
- Status tracking works correctly.
- Email notifications are triggered properly.
- Dashboard metrics are accurate.
- Audit trail captures all required actions.
- Role-based access works as expected.

---

## 15. Approval

| Name | Role | Approval Status |
|---|---|---|
| Product Owner | Business Owner | Pending |
| Operations Manager | Business Stakeholder | Pending |
| Compliance Lead | Compliance Reviewer | Pending |
| QA Lead | Testing Owner | Pending |
| Business Analyst | Document Owner | Drafted |