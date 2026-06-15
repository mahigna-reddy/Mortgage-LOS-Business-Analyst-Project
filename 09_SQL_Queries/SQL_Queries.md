# SQL Queries Document

## Project Name

Digital Mortgage Loan Origination & Applicant Tracking System

## Document Type

SQL Queries Document

## Domain

Banking / Mortgage / Financial Services

---

## 1. Purpose

This document contains sample SQL queries used by the Business Analyst to validate mortgage loan application data, application status, document status, underwriting decisions, dashboard metrics, audit trail records, and reporting outputs.

These queries support data validation, UAT testing, defect analysis, reporting verification, and requirement traceability.

---

## 2. Assumed Database Tables

The following sample database tables are used for this project:

| Table Name                 | Purpose                                  |
| -------------------------- | ---------------------------------------- |
| borrowers                  | Stores borrower profile details          |
| loan_applications          | Stores mortgage loan application details |
| application_documents      | Stores uploaded document details         |
| application_status_history | Stores status change history             |
| audit_log                  | Stores audit trail records               |
| users                      | Stores internal user details             |
| notifications              | Stores email notification history        |

---

## 3. Borrower Validation Queries

### Query 1: Get borrower details by borrower ID

```sql
SELECT 
    borrower_id,
    borrower_full_name,
    borrower_email,
    borrower_phone,
    registration_date
FROM borrowers
WHERE borrower_id = 'BORR1001';
```

### Query 2: Check duplicate borrower email

```sql
SELECT 
    borrower_email,
    COUNT(*) AS email_count
FROM borrowers
GROUP BY borrower_email
HAVING COUNT(*) > 1;
```

### Query 3: Validate borrower phone number length

```sql
SELECT 
    borrower_id,
    borrower_full_name,
    borrower_phone
FROM borrowers
WHERE LENGTH(borrower_phone) <> 10;
```

---

## 4. Loan Application Validation Queries

### Query 4: Get all submitted loan applications

```sql
SELECT 
    application_id,
    borrower_id,
    applicant_full_name,
    requested_loan_amount,
    loan_purpose,
    application_status,
    submitted_date
FROM loan_applications
WHERE application_status = 'Submitted';
```

### Query 5: Get loan application by application ID

```sql
SELECT 
    application_id,
    borrower_id,
    applicant_full_name,
    applicant_email,
    requested_loan_amount,
    loan_purpose,
    property_type,
    application_status,
    submitted_date
FROM loan_applications
WHERE application_id = 'LN100245';
```

### Query 6: Validate loan amount greater than zero

```sql
SELECT 
    application_id,
    applicant_full_name,
    requested_loan_amount
FROM loan_applications
WHERE requested_loan_amount <= 0
   OR requested_loan_amount IS NULL;
```

### Query 7: Validate annual income greater than zero

```sql
SELECT 
    application_id,
    applicant_full_name,
    annual_income
FROM loan_applications
WHERE annual_income <= 0
   OR annual_income IS NULL;
```

### Query 8: Get loan applications submitted in current month

```sql
SELECT 
    application_id,
    applicant_full_name,
    requested_loan_amount,
    application_status,
    submitted_date
FROM loan_applications
WHERE submitted_date >= DATE_TRUNC('month', CURRENT_DATE)
ORDER BY submitted_date DESC;
```

---

## 5. Document Upload Validation Queries

### Query 9: Get documents uploaded for an application

```sql
SELECT 
    document_id,
    application_id,
    document_type,
    file_name,
    file_size_mb,
    upload_status,
    uploaded_date
FROM application_documents
WHERE application_id = 'LN100245';
```

### Query 10: Find applications with pending documents

```sql
SELECT 
    la.application_id,
    la.applicant_full_name,
    la.application_status,
    ad.document_type,
    ad.upload_status
FROM loan_applications la
LEFT JOIN application_documents ad
    ON la.application_id = ad.application_id
WHERE la.application_status = 'Pending Documents';
```

### Query 11: Validate unsupported document formats

```sql
SELECT 
    document_id,
    application_id,
    document_type,
    file_name
FROM application_documents
WHERE LOWER(file_name) NOT LIKE '%.pdf'
  AND LOWER(file_name) NOT LIKE '%.jpg'
  AND LOWER(file_name) NOT LIKE '%.png';
```

### Query 12: Validate document file size greater than 10 MB

```sql
SELECT 
    document_id,
    application_id,
    document_type,
    file_name,
    file_size_mb
FROM application_documents
WHERE file_size_mb > 10;
```

---

## 6. Application Status Validation Queries

### Query 13: Count applications by status

```sql
SELECT 
    application_status,
    COUNT(*) AS total_applications
FROM loan_applications
GROUP BY application_status
ORDER BY total_applications DESC;
```

### Query 14: Get applications currently in underwriting

```sql
SELECT 
    application_id,
    applicant_full_name,
    requested_loan_amount,
    assigned_underwriter,
    submitted_date,
    application_status
FROM loan_applications
WHERE application_status = 'Underwriting';
```

### Query 15: Get approved applications

```sql
SELECT 
    application_id,
    applicant_full_name,
    requested_loan_amount,
    decision_date,
    assigned_underwriter
FROM loan_applications
WHERE application_status = 'Approved'
ORDER BY decision_date DESC;
```

### Query 16: Get rejected applications with rejection reason

```sql
SELECT 
    application_id,
    applicant_full_name,
    requested_loan_amount,
    decision_date,
    rejection_reason,
    assigned_underwriter
FROM loan_applications
WHERE application_status = 'Rejected'
ORDER BY decision_date DESC;
```

---

## 7. Loan Officer Queue Queries

### Query 17: Get loan officer review queue

```sql
SELECT 
    application_id,
    applicant_full_name,
    requested_loan_amount,
    application_status,
    document_status,
    submitted_date,
    assigned_loan_officer
FROM loan_applications
WHERE application_status IN ('Submitted', 'In Review', 'Pending Documents')
ORDER BY submitted_date ASC;
```

### Query 18: Get applications assigned to a specific loan officer

```sql
SELECT 
    application_id,
    applicant_full_name,
    requested_loan_amount,
    application_status,
    document_status,
    submitted_date
FROM loan_applications
WHERE assigned_loan_officer = 'LO102'
ORDER BY submitted_date DESC;
```

---

## 8. Underwriter Queue Queries

### Query 19: Get underwriter queue

```sql
SELECT 
    application_id,
    applicant_full_name,
    requested_loan_amount,
    annual_income,
    property_type,
    application_status,
    assigned_underwriter
FROM loan_applications
WHERE application_status = 'Underwriting'
ORDER BY submitted_date ASC;
```

### Query 20: Get applications assigned to a specific underwriter

```sql
SELECT 
    application_id,
    applicant_full_name,
    requested_loan_amount,
    application_status,
    submitted_date,
    decision_date
FROM loan_applications
WHERE assigned_underwriter = 'UW204'
ORDER BY submitted_date DESC;
```

---

## 9. Dashboard Reporting Queries

### Query 21: Loan pipeline dashboard summary

```sql
SELECT 
    COUNT(*) AS total_applications,
    SUM(CASE WHEN application_status = 'Submitted' THEN 1 ELSE 0 END) AS submitted_count,
    SUM(CASE WHEN application_status = 'Pending Documents' THEN 1 ELSE 0 END) AS pending_documents_count,
    SUM(CASE WHEN application_status = 'In Review' THEN 1 ELSE 0 END) AS in_review_count,
    SUM(CASE WHEN application_status = 'Underwriting' THEN 1 ELSE 0 END) AS underwriting_count,
    SUM(CASE WHEN application_status = 'Approved' THEN 1 ELSE 0 END) AS approved_count,
    SUM(CASE WHEN application_status = 'Rejected' THEN 1 ELSE 0 END) AS rejected_count
FROM loan_applications;
```

### Query 22: Total loan amount by status

```sql
SELECT 
    application_status,
    COUNT(*) AS total_applications,
    SUM(requested_loan_amount) AS total_requested_loan_amount
FROM loan_applications
GROUP BY application_status
ORDER BY total_requested_loan_amount DESC;
```

### Query 23: Application aging report

```sql
SELECT 
    application_id,
    applicant_full_name,
    application_status,
    submitted_date,
    CURRENT_DATE - submitted_date AS pending_days,
    assigned_loan_officer,
    assigned_underwriter
FROM loan_applications
WHERE application_status NOT IN ('Approved', 'Rejected', 'Withdrawn')
ORDER BY pending_days DESC;
```

### Query 24: SLA breached applications

```sql
SELECT 
    application_id,
    applicant_full_name,
    application_status,
    submitted_date,
    CURRENT_DATE - submitted_date AS pending_days
FROM loan_applications
WHERE application_status NOT IN ('Approved', 'Rejected', 'Withdrawn')
  AND CURRENT_DATE - submitted_date > 7
ORDER BY pending_days DESC;
```

---

## 10. Audit Trail Queries

### Query 25: Get audit trail for one loan application

```sql
SELECT 
    application_id,
    user_id,
    user_role,
    action_type,
    old_value,
    new_value,
    action_timestamp,
    comments
FROM audit_log
WHERE application_id = 'LN100245'
ORDER BY action_timestamp DESC;
```

### Query 26: Validate status change history

```sql
SELECT 
    application_id,
    old_status,
    new_status,
    updated_by,
    updated_timestamp,
    comments
FROM application_status_history
WHERE application_id = 'LN100245'
ORDER BY updated_timestamp ASC;
```

### Query 27: Get all underwriter decision audit records

```sql
SELECT 
    application_id,
    user_id,
    user_role,
    action_type,
    old_value,
    new_value,
    action_timestamp,
    comments
FROM audit_log
WHERE user_role = 'Underwriter'
  AND action_type = 'DECISION'
ORDER BY action_timestamp DESC;
```

---

## 11. Notification Validation Queries

### Query 28: Get notification history for application

```sql
SELECT 
    notification_id,
    application_id,
    recipient_email,
    notification_type,
    notification_status,
    sent_timestamp
FROM notifications
WHERE application_id = 'LN100245'
ORDER BY sent_timestamp DESC;
```

### Query 29: Find failed notifications

```sql
SELECT 
    notification_id,
    application_id,
    recipient_email,
    notification_type,
    notification_status,
    error_message,
    sent_timestamp
FROM notifications
WHERE notification_status = 'Failed'
ORDER BY sent_timestamp DESC;
```

---

## 12. Data Quality Validation Queries

### Query 30: Find applications with missing mandatory fields

```sql
SELECT 
    application_id,
    applicant_full_name,
    applicant_email,
    requested_loan_amount,
    annual_income,
    application_status
FROM loan_applications
WHERE applicant_full_name IS NULL
   OR applicant_email IS NULL
   OR requested_loan_amount IS NULL
   OR annual_income IS NULL;
```

### Query 31: Validate invalid email format

```sql
SELECT 
    application_id,
    applicant_full_name,
    applicant_email
FROM loan_applications
WHERE applicant_email NOT LIKE '%@%.%';
```

### Query 32: Validate SSN last four digits

```sql
SELECT 
    application_id,
    applicant_full_name,
    ssn_last_four
FROM loan_applications
WHERE LENGTH(ssn_last_four) <> 4;
```

---

## 13. UAT Support Queries

### Query 33: Verify application after borrower submission

```sql
SELECT 
    application_id,
    borrower_id,
    applicant_full_name,
    application_status,
    submitted_date
FROM loan_applications
WHERE borrower_id = 'BORR1001'
ORDER BY submitted_date DESC;
```

### Query 34: Verify status after loan officer moves application to underwriting

```sql
SELECT 
    application_id,
    application_status,
    assigned_loan_officer,
    assigned_underwriter,
    updated_date
FROM loan_applications
WHERE application_id = 'LN100245';
```

### Query 35: Verify dashboard count after approval

```sql
SELECT 
    application_status,
    COUNT(*) AS total_count
FROM loan_applications
WHERE application_status IN ('Approved', 'Rejected', 'Underwriting')
GROUP BY application_status;
```

---

## 14. BA Notes

As a Business Analyst, these SQL queries help to:

* Validate borrower and loan application data.
* Support UAT testing and business sign-off.
* Verify dashboard and reporting accuracy.
* Investigate defects reported by QA or business users.
* Confirm document upload and status update behavior.
* Validate audit trail and notification records.
* Support data mapping and requirement traceability.
