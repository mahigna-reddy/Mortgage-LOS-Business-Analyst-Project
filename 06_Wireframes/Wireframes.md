# Wireframes

## Project Name

Digital Mortgage Loan Origination & Applicant Tracking System

## Document Type

Wireframe Requirements Document

## Domain

Banking / Mortgage / Financial Services

---

## 1. Purpose

This document defines the wireframe requirements for the Mortgage Loan Origination System enhancement.

The purpose of wireframes is to show the expected screen layout, fields, buttons, validations, and business rules before development starts.

These wireframes help business stakeholders, product owners, developers, QA teams, and UAT users understand how each screen should behave.

---

## 2. Wireframe List

The project includes the following screens:

| Screen ID | Screen Name | User Role |
|---|---|---|
| WF-001 | Borrower Registration Page | Borrower |
| WF-002 | Borrower Login Page | Borrower |
| WF-003 | Borrower Dashboard | Borrower |
| WF-004 | Mortgage Application Form | Borrower |
| WF-005 | Document Upload Page | Borrower |
| WF-006 | Application Status Tracking Page | Borrower |
| WF-007 | Loan Officer Review Dashboard | Loan Officer |
| WF-008 | Loan Officer Application Review Page | Loan Officer |
| WF-009 | Underwriter Queue Page | Underwriter |
| WF-010 | Underwriter Decision Page | Underwriter |
| WF-011 | Operations Manager Dashboard | Operations Manager |
| WF-012 | Audit Trail Page | Compliance User |

---

## WF-001: Borrower Registration Page

### Purpose

Allows a new borrower to create an account in the mortgage portal.

### Fields

| Field Name | Field Type | Required |
|---|---|---|
| Full Name | Text Box | Yes |
| Email Address | Text Box | Yes |
| Phone Number | Text Box | Yes |
| Password | Password Field | Yes |
| Confirm Password | Password Field | Yes |

### Buttons

| Button | Action |
|---|---|
| Register | Creates borrower account |
| Clear | Clears entered values |
| Login | Redirects to login page |

### Validation Rules

- Full name is mandatory.
- Email address must be in valid email format.
- Phone number must contain 10 digits.
- Password and confirm password must match.
- Password must meet minimum security requirements.

### Business Rules

- Duplicate email registration should not be allowed.
- Borrower profile should be created after successful registration.
- Registration confirmation email should be sent to borrower.

---

## WF-002: Borrower Login Page

### Purpose

Allows registered borrowers to log in and access their dashboard.

### Fields

| Field Name | Field Type | Required |
|---|---|---|
| Email Address | Text Box | Yes |
| Password | Password Field | Yes |

### Buttons

| Button | Action |
|---|---|
| Login | Authenticates borrower |
| Forgot Password | Starts password reset process |
| Register | Redirects to registration page |

### Validation Rules

- Email and password are mandatory.
- Invalid login should display error message.
- User should not access dashboard without login.

### Business Rules

- User session should expire after inactivity.
- Borrower should only see their own applications.

---

## WF-003: Borrower Dashboard

### Purpose

Displays borrower applications, status, and available actions.

### Display Elements

| Element | Description |
|---|---|
| Welcome Message | Displays borrower name |
| New Application Button | Allows borrower to start new loan application |
| Application List | Shows submitted and draft applications |
| Status Column | Shows current application status |
| Action Column | Allows borrower to view or continue application |

### Buttons

| Button | Action |
|---|---|
| New Application | Starts new application |
| View Application | Opens submitted application |
| Continue Draft | Opens draft application |
| Upload Documents | Opens document upload page |

### Business Rules

- Draft applications should be editable.
- Submitted applications should be view-only for borrower.
- Borrower should see only their own loan applications.

---

## WF-004: Mortgage Application Form

### Purpose

Allows borrower to enter personal, employment, income, property, and loan details.

### Sections

1. Personal Details
2. Employment Details
3. Income Details
4. Property Details
5. Loan Details

### Personal Details Fields

| Field Name | Field Type | Required |
|---|---|---|
| Full Name | Text Box | Yes |
| Date of Birth | Date Picker | Yes |
| Email | Text Box | Yes |
| Phone Number | Text Box | Yes |
| SSN Last Four Digits | Text Box | Yes |

### Employment Details Fields

| Field Name | Field Type | Required |
|---|---|---|
| Employer Name | Text Box | Yes |
| Employment Type | Dropdown | Yes |
| Job Title | Text Box | Yes |
| Years Employed | Number Field | Yes |

### Income Details Fields

| Field Name | Field Type | Required |
|---|---|---|
| Annual Income | Number Field | Yes |
| Monthly Income | Number Field | Yes |
| Additional Income | Number Field | No |

### Property Details Fields

| Field Name | Field Type | Required |
|---|---|---|
| Property Address | Text Area | Yes |
| Property Type | Dropdown | Yes |
| Purchase Price | Number Field | Yes |
| Occupancy Type | Dropdown | Yes |

### Loan Details Fields

| Field Name | Field Type | Required |
|---|---|---|
| Loan Amount | Number Field | Yes |
| Loan Purpose | Dropdown | Yes |
| Down Payment | Number Field | Yes |
| Loan Term | Dropdown | Yes |

### Buttons

| Button | Action |
|---|---|
| Save as Draft | Saves incomplete application |
| Next | Moves to next section |
| Back | Goes to previous section |
| Submit Application | Submits completed application |

### Validation Rules

- Mandatory fields cannot be blank.
- Loan amount must be greater than zero.
- Annual income must be greater than zero.
- Phone number must contain 10 digits.
- SSN should accept only last four digits.

### Business Rules

- Application starts in Draft status.
- Application changes to Submitted after final submission.
- Unique application ID should be generated after submission.
- Borrower cannot edit application after submission.

---

## WF-005: Document Upload Page

### Purpose

Allows borrower to upload required mortgage documents.

### Fields

| Field Name | Field Type | Required |
|---|---|---|
| Application ID | Read Only | Yes |
| Document Type | Dropdown | Yes |
| Upload File | File Upload | Yes |
| Upload Status | Read Only | Yes |
| Uploaded Date | Read Only | No |

### Document Types

- Pay Stubs
- W2
- Bank Statements
- Tax Returns
- Government ID
- Property Documents
- Additional Supporting Documents

### Buttons

| Button | Action |
|---|---|
| Upload | Uploads selected document |
| Delete | Deletes document before submission |
| Submit Documents | Confirms uploaded documents |
| Back to Dashboard | Returns to dashboard |

### Validation Rules

- File type must be PDF, JPG, or PNG.
- File size should not exceed 10 MB.
- Required documents must be uploaded before application moves forward.

### Business Rules

- Borrower can delete documents only before final submission.
- Loan officer should be able to view uploaded documents.
- Document upload action should be captured in audit trail.

---

## WF-006: Application Status Tracking Page

### Purpose

Allows borrower to view current loan application status.

### Display Fields

| Field Name | Description |
|---|---|
| Application ID | Unique loan application number |
| Submitted Date | Date application was submitted |
| Current Status | Current application status |
| Last Updated Date | Last status update date |
| Action Required | Shows if borrower needs to upload documents or provide info |

### Status Values

- Draft
- Submitted
- Pending Documents
- In Review
- Underwriting
- Additional Info Required
- Approved
- Rejected
- Withdrawn

### Business Rules

- Borrower should not see internal comments.
- Borrower should see only external status messages.
- If action is required, system should show next step clearly.

---

## WF-007: Loan Officer Review Dashboard

### Purpose

Allows loan officers to view and manage submitted applications.

### Display Columns

| Column | Description |
|---|---|
| Application ID | Unique application number |
| Borrower Name | Applicant name |
| Loan Amount | Requested loan amount |
| Status | Current application status |
| Submitted Date | Date submitted |
| Document Status | Complete or Pending |
| Assigned Loan Officer | Assigned user |
| Action | Review button |

### Filters

- Status
- Submitted Date
- Document Status
- Loan Amount Range
- Borrower Name

### Buttons

| Button | Action |
|---|---|
| Review | Opens application details |
| Request Documents | Requests missing documents |
| Move to Underwriting | Sends application to underwriter |

### Business Rules

- Loan officer can review but cannot approve or reject applications.
- Incomplete applications cannot move to underwriting.
- Missing document request should notify borrower.

---

## WF-008: Loan Officer Application Review Page

### Purpose

Allows loan officer to review borrower details and documents.

### Sections

- Borrower Details
- Employment and Income Details
- Property and Loan Details
- Uploaded Documents
- Loan Officer Comments
- Action Panel

### Buttons

| Button | Action |
|---|---|
| Add Comment | Saves loan officer comments |
| Request Missing Documents | Sends request to borrower |
| Move to Underwriting | Updates status to Underwriting |
| Back to Queue | Returns to dashboard |

### Business Rules

- Comments should be saved with timestamp.
- Status change should be captured in audit trail.
- Borrower should receive notification for missing documents or underwriting movement.

---

## WF-009: Underwriter Queue Page

### Purpose

Allows underwriters to view applications ready for underwriting.

### Display Columns

| Column | Description |
|---|---|
| Application ID | Unique application number |
| Borrower Name | Applicant name |
| Loan Amount | Requested loan amount |
| Status | Underwriting |
| Assigned Underwriter | Assigned user |
| Received Date | Date moved to underwriting |
| Action | Review button |

### Filters

- Received Date
- Loan Amount Range
- Assigned Underwriter
- Application Status

### Business Rules

- Only applications in Underwriting status should appear.
- Underwriter should be able to open application details.
- Underwriter decision should update application status.

---

## WF-010: Underwriter Decision Page

### Purpose

Allows underwriter to approve, reject, or request more information.

### Sections

- Application Summary
- Borrower Details
- Income and Employment Details
- Property and Loan Details
- Uploaded Documents
- Underwriter Comments
- Decision Panel

### Decision Options

- Approve
- Reject
- Request Additional Information

### Buttons

| Button | Action |
|---|---|
| Approve | Updates status to Approved |
| Reject | Updates status to Rejected |
| Request More Info | Updates status to Additional Info Required |
| Save Comment | Saves underwriter comments |
| Back to Queue | Returns to underwriting queue |

### Validation Rules

- Rejection comments are mandatory.
- Comments are mandatory when requesting additional information.
- Decision cannot be submitted without selecting an option.

### Business Rules

- Only underwriters can approve or reject loans.
- Borrower should receive notification after decision.
- Decision should update dashboard metrics.
- Decision should be captured in audit trail.

---

## WF-011: Operations Manager Dashboard

### Purpose

Allows operations managers to monitor loan pipeline and application volume.

### Dashboard Metrics

| Metric | Description |
|---|---|
| Total Applications | Total submitted applications |
| Pending Documents | Applications waiting for documents |
| In Review | Applications under loan officer review |
| Underwriting | Applications under underwriting |
| Approved Loans | Approved application count |
| Rejected Loans | Rejected application count |
| SLA Breached | Applications pending beyond SLA |
| Average Processing Time | Average time from submission to decision |

### Filters

- Date Range
- Application Status
- Loan Officer
- Underwriter
- Loan Amount Range

### Buttons

| Button | Action |
|---|---|
| Apply Filter | Refreshes dashboard |
| Export Report | Exports report to Excel |
| View Details | Opens detailed report |

### Business Rules

- Manager can view reports but cannot update loan decision.
- Dashboard should refresh based on latest application status.
- Exported report should match dashboard filters.

---

## WF-012: Audit Trail Page

### Purpose

Allows compliance users to review application history and status changes.

### Search Fields

| Field | Description |
|---|---|
| Application ID | Search by loan application number |
| Borrower Name | Search by applicant name |
| Date Range | Search by action date |
| User Role | Filter by borrower, loan officer, underwriter, manager |
| Action Type | Filter by status change, upload, decision, comment |

### Display Columns

| Column | Description |
|---|---|
| Application ID | Loan application number |
| User ID | User who performed action |
| User Role | Role of user |
| Action Type | Type of action performed |
| Old Value | Previous value |
| New Value | Updated value |
| Timestamp | Date and time of action |
| Comments | User comments if available |

### Business Rules

- Audit records should be read-only.
- Compliance users cannot edit borrower or loan data.
- Audit trail should capture status updates, document uploads, comments, and decisions.

---

## 3. BA Notes

These wireframe requirements help the team understand:

- What screens are needed
- What fields should be available
- What buttons/actions are required
- What validations should happen
- What business rules apply to each screen
- What QA should validate during testing