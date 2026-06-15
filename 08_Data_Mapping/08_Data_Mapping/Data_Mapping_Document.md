# Data Mapping Document

## Project Name

Digital Mortgage Loan Origination & Applicant Tracking System

## Document Type

Data Mapping Document

## Domain

Banking / Mortgage / Financial Services

---

## 1. Purpose

This document defines the source-to-target data mapping for the Mortgage Loan Origination System enhancement.

The purpose of this document is to help business, development, QA, reporting, and data teams understand how borrower, loan, document, status, and audit data flows between different systems.

As a Business Analyst, this document supports requirement clarification, data validation, API mapping, reporting accuracy, and UAT test preparation.

---

## 2. Systems Involved

| System | Description |
|---|---|
| Borrower Web Portal | Frontend application used by borrowers |
| Loan Origination System Database | Core database where loan application data is stored |
| Document Management System | Stores uploaded borrower documents |
| Underwriting System | Used by underwriters to review loan risk and decisions |
| Notification Service | Sends email notifications to borrowers |
| Reporting Dashboard | Displays loan pipeline metrics |
| Audit Log Database | Stores all status changes and user actions |

---

## 3. Borrower Registration Data Mapping

| Source Field | Source System | Target Field | Target System | Data Type | Transformation Rule | Mandatory | Business Rule |
|---|---|---|---|---|---|---|---|
| fullName | Borrower Web Portal | borrower_full_name | LOS Database | String | Trim spaces | Yes | Required for borrower profile |
| email | Borrower Web Portal | borrower_email | LOS Database | String | Convert to lowercase | Yes | Must be unique |
| phoneNumber | Borrower Web Portal | borrower_phone | LOS Database | String | Remove spaces/special characters | Yes | Must be 10 digits |
| password | Borrower Web Portal | password_hash | Authentication Service | String | Encrypt/hash password | Yes | Must meet security rules |
| registrationDate | System Generated | registration_date | LOS Database | DateTime | System timestamp | Yes | Captured after successful registration |
| borrowerId | System Generated | borrower_id | LOS Database | String | Generate unique ID | Yes | Unique borrower identifier |

---

## 4. Loan Application Data Mapping

| Source Field | Source System | Target Field | Target System | Data Type | Transformation Rule | Mandatory | Business Rule |
|---|---|---|---|---|---|---|---|
| borrowerId | Borrower Web Portal | borrower_id | LOS Database | String | No transformation | Yes | Must exist before application submission |
| fullName | Borrower Web Portal | applicant_full_name | LOS Database | String | Trim spaces | Yes | Required |
| dateOfBirth | Borrower Web Portal | date_of_birth | LOS Database | Date | Convert to YYYY-MM-DD | Yes | Required for identity verification |
| email | Borrower Web Portal | applicant_email | LOS Database | String | Convert to lowercase | Yes | Must be valid email |
| phoneNumber | Borrower Web Portal | applicant_phone | LOS Database | String | Remove spaces/special characters | Yes | Must be 10 digits |
| ssnLastFour | Borrower Web Portal | ssn_last_four | LOS Database | String | Mask full SSN, store last four only | Yes | Only last four digits allowed |
| employerName | Borrower Web Portal | employer_name | LOS Database | String | Trim spaces | Yes | Required for employment verification |
| employmentType | Borrower Web Portal | employment_type | LOS Database | String | Map dropdown value | Yes | Full Time, Part Time, Self Employed |
| jobTitle | Borrower Web Portal | job_title | LOS Database | String | Trim spaces | Yes | Required |
| yearsEmployed | Borrower Web Portal | years_employed | LOS Database | Number | No transformation | Yes | Must be 0 or greater |
| annualIncome | Borrower Web Portal | annual_income | LOS Database | Decimal | Format to 2 decimals | Yes | Must be greater than 0 |
| monthlyIncome | Borrower Web Portal | monthly_income | LOS Database | Decimal | Format to 2 decimals | Yes | Must be greater than 0 |
| additionalIncome | Borrower Web Portal | additional_income | LOS Database | Decimal | Default to 0 if blank | No | Optional |
| propertyAddress | Borrower Web Portal | property_address | LOS Database | String | Trim spaces | Yes | Required |
| propertyType | Borrower Web Portal | property_type | LOS Database | String | Map dropdown value | Yes | Single Family, Condo, Townhome |
| purchasePrice | Borrower Web Portal | purchase_price | LOS Database | Decimal | Format to 2 decimals | Yes | Must be greater than 0 |
| occupancyType | Borrower Web Portal | occupancy_type | LOS Database | String | Map dropdown value | Yes | Primary, Secondary, Investment |
| loanAmount | Borrower Web Portal | requested_loan_amount | LOS Database | Decimal | Format to 2 decimals | Yes | Must be greater than 0 |
| loanPurpose | Borrower Web Portal | loan_purpose | LOS Database | String | Map dropdown value | Yes | Home Purchase or Refinance |
| downPayment | Borrower Web Portal | down_payment_amount | LOS Database | Decimal | Format to 2 decimals | Yes | Must be 0 or greater |
| loanTerm | Borrower Web Portal | loan_term | LOS Database | String | Map dropdown value | Yes | 15 Years or 30 Years |

---

## 5. Document Upload Data Mapping

| Source Field | Source System | Target Field | Target System | Data Type | Transformation Rule | Mandatory | Business Rule |
|---|---|---|---|---|---|---|---|
| applicationId | Borrower Web Portal | application_id | Document Management System | String | No transformation | Yes | Must be valid application |
| documentType | Borrower Web Portal | document_type | Document Management System | String | Map dropdown value | Yes | Required before upload |
| fileName | Borrower Web Portal | file_name | Document Management System | String | Preserve original file name | Yes | Must have valid extension |
| fileContent | Borrower Web Portal | document_file | Document Management System | File | Store as binary/file object | Yes | PDF, JPG, PNG only |
| fileSize | System Generated | file_size_mb | Document Management System | Decimal | Convert bytes to MB | Yes | Must be <= 10 MB |
| uploadedDate | System Generated | uploaded_date | Document Management System | DateTime | System timestamp | Yes | Capture upload time |
| uploadStatus | System Generated | upload_status | Document Management System | String | Default to Submitted | Yes | Submitted, Failed, Deleted |
| uploadedBy | System Generated | uploaded_by | Audit Log Database | String | Capture user ID | Yes | Required for audit |

---

## 6. Application Status Data Mapping

| Source Field | Source System | Target Field | Target System | Data Type | Transformation Rule | Mandatory | Business Rule |
|---|---|---|---|---|---|---|---|
| applicationId | LOS Database | application_id | Reporting Dashboard | String | No transformation | Yes | Unique application ID |
| currentStatus | LOS Database | current_status | Reporting Dashboard | String | Map status code to label | Yes | Used for dashboard count |
| oldStatus | LOS Database | old_status | Audit Log Database | String | Capture previous status | Yes | Required for audit |
| newStatus | User Action | new_status | Audit Log Database | String | Capture updated status | Yes | Required for audit |
| updatedBy | User Action | updated_by | Audit Log Database | String | Capture user ID | Yes | Required for audit |
| userRole | User Action | user_role | Audit Log Database | String | Capture role | Yes | Borrower, Loan Officer, Underwriter |
| comments | User Action | comments | Audit Log Database | String | Trim spaces | Conditional | Required for rejection |
| updatedDate | System Generated | updated_timestamp | Audit Log Database | DateTime | System timestamp | Yes | Required for audit |

---

## 7. Dashboard Data Mapping

| Source Field | Source System | Target Field | Target System | Data Type | Transformation Rule | Mandatory | Business Rule |
|---|---|---|---|---|---|---|---|
| application_id | LOS Database | applicationId | Reporting Dashboard | String | No transformation | Yes | Used for drill-down |
| application_status | LOS Database | status | Reporting Dashboard | String | Map status code to display label | Yes | Used for status count |
| submitted_date | LOS Database | submittedDate | Reporting Dashboard | Date | Format as MM/DD/YYYY | Yes | Used for date filter |
| loan_amount | LOS Database | loanAmount | Reporting Dashboard | Decimal | Format as currency | Yes | Used for loan volume |
| assigned_loan_officer | LOS Database | loanOfficer | Reporting Dashboard | String | Map user ID to name | No | Used for filter |
| assigned_underwriter | LOS Database | underwriter | Reporting Dashboard | String | Map user ID to name | No | Used for filter |
| decision_date | LOS Database | decisionDate | Reporting Dashboard | Date | Format as MM/DD/YYYY | No | Used for approved/rejected report |
| sla_days | Calculated Field | pendingDays | Reporting Dashboard | Number | Current date - submitted date | Yes | Used for aging report |

---

## 8. Notification Data Mapping

| Source Field | Source System | Target Field | Target System | Data Type | Transformation Rule | Mandatory | Business Rule |
|---|---|---|---|---|---|---|---|
| borrowerEmail | LOS Database | recipient_email | Notification Service | String | Convert to lowercase | Yes | Required to send email |
| borrowerName | LOS Database | recipient_name | Notification Service | String | Trim spaces | Yes | Used in email template |
| applicationId | LOS Database | application_id | Notification Service | String | No transformation | Yes | Included in email |
| newStatus | LOS Database | application_status | Notification Service | String | Map status to user-friendly label | Yes | Included in email |
| notificationType | System Generated | notification_type | Notification Service | String | Based on status change | Yes | Submitted, Approved, Rejected, Pending Docs |
| sentDate | System Generated | sent_timestamp | Notification Service | DateTime | System timestamp | Yes | Required for tracking |

---

## 9. Audit Trail Data Mapping

| Source Field | Source System | Target Field | Target System | Data Type | Transformation Rule | Mandatory | Business Rule |
|---|---|---|---|---|---|---|---|
| applicationId | LOS Database | application_id | Audit Log Database | String | No transformation | Yes | Required |
| userId | User Session | user_id | Audit Log Database | String | No transformation | Yes | Required |
| userRole | User Session | user_role | Audit Log Database | String | No transformation | Yes | Required |
| actionType | System Generated | action_type | Audit Log Database | String | Map action type | Yes | STATUS_UPDATE, DOCUMENT_UPLOAD, DECISION |
| oldValue | System Generated | old_value | Audit Log Database | String | Capture before change | Conditional | Required for status changes |
| newValue | User Action | new_value | Audit Log Database | String | Capture after change | Conditional | Required for status changes |
| timestamp | System Generated | action_timestamp | Audit Log Database | DateTime | System timestamp | Yes | Required |
| comments | User Action | comments | Audit Log Database | String | Trim spaces | No | Required for rejection |

---

## 10. Data Quality Rules

| Rule ID | Rule Description |
|---|---|
| DQ-001 | Email fields should be stored in lowercase format. |
| DQ-002 | Phone numbers should be stored as 10 digits without special characters. |
| DQ-003 | Amount fields should be stored with two decimal places. |
| DQ-004 | Date fields should follow standard database date format. |
| DQ-005 | SSN should store only last four digits. |
| DQ-006 | Required fields should not be null. |
| DQ-007 | Application status should match approved status values only. |
| DQ-008 | Audit records should not be deleted or modified. |

---

## 11. BA Notes

As a Business Analyst, this data mapping document helps to:

- Clarify how data moves from source systems to target systems.
- Support developers during API and database design.
- Support QA team during data validation.
- Help reporting teams validate dashboard metrics.
- Support UAT scenarios involving borrower data, status updates, documents, and reports.
- Maintain traceability between frontend fields, backend database fields, and reporting outputs.