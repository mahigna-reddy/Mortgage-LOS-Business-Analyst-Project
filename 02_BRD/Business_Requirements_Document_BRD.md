# Business Requirements Document

## Project Name

Digital Mortgage Loan Origination & Applicant Tracking System

## Document Type

Business Requirements Document

## Domain

Banking / Mortgage / Financial Services


---

## 1. Introduction

This Business Requirements Document defines the business needs, objectives, scope, stakeholders, and high-level requirements for enhancing a Mortgage Loan Origination System.

The purpose of this project is to improve the mortgage loan application process by allowing borrowers to submit loan applications online, upload required documents, track application status, and receive automated notifications.

The enhanced system will also support internal users such as loan officers, underwriters, compliance teams, and operations managers by providing better visibility, workflow tracking, audit history, and reporting.

---

## 2. Business Need

The existing mortgage loan process includes several manual steps and delays. Borrowers often need to contact loan officers directly to check application status or confirm missing documents. Internal teams spend significant time manually tracking loan applications, reviewing documents, and sending follow-up emails.

The business needs a centralized digital platform that improves application submission, document tracking, underwriting review, status updates, and loan pipeline reporting.

---

## 3. Current State

In the current process:

- Borrowers submit loan information through limited online forms or manual channels.
- Loan officers manually review application details.
- Missing documents are tracked through email or spreadsheets.
- Borrowers do not have real-time visibility into application status.
- Underwriters manually review documents and update decisions.
- Managers have limited dashboard visibility into pending, approved, and rejected loans.
- Audit history is not consistently captured for every status change.
- Reporting requires manual data extraction and spreadsheet updates.

---

## 4. Future State

In the future state:

- Borrowers can submit mortgage applications online.
- Borrowers can upload required documents directly through the system.
- Loan officers can review applications and move them to underwriting.
- Underwriters can approve, reject, or request additional documents.
- Borrowers can track loan status in real time.
- Automated notifications will be sent when status changes occur.
- All status updates and decisions will be captured in an audit trail.
- Operations managers can view loan pipeline dashboards and reports.

---

## 5. Business Objectives

The business objectives are:

- Improve borrower experience by providing digital application submission and status tracking.
- Reduce manual follow-ups between borrowers and internal teams.
- Improve loan officer and underwriter productivity.
- Reduce delays caused by missing documents.
- Improve audit traceability for compliance.
- Provide real-time reporting for loan pipeline management.
- Standardize the mortgage application review workflow.

---

## 6. Stakeholders

| Stakeholder | Role / Responsibility |
|---|---|
| Borrower | Submits loan application and uploads documents |
| Loan Officer | Reviews application completeness and borrower information |
| Underwriter | Reviews loan risk and makes decision |
| Compliance Team | Validates audit and regulatory requirements |
| Operations Manager | Monitors loan pipeline and team performance |
| Product Owner | Owns product backlog and business priorities |
| Business Analyst | Documents requirements, workflows, and UAT support |
| Development Team | Builds the required system enhancements |
| QA Team | Validates functionality through testing |

---

## 7. Scope

### In Scope

The project includes:

- Borrower registration and login
- Mortgage loan application submission
- Employment, income, property, and loan details capture
- Document upload functionality
- Loan officer review workflow
- Underwriter decision workflow
- Application status tracking
- Automated email notifications
- Audit trail for status changes
- Manager dashboard and reporting
- API requirement documentation
- UAT test scenarios
- Requirement traceability matrix

### Out of Scope

The project does not include:

- Credit bureau integration
- Payment processing
- Loan closing document generation
- Mobile application development
- AI-based underwriting
- Appraisal vendor integration
- Title vendor integration

---

## 8. Assumptions

- Borrowers will have access to a valid email address for registration and notifications.
- Internal users will be assigned role-based access.
- Required mortgage document types will be provided by the business team.
- Email notification service will be available for integration.
- Dashboard data will be sourced from the Loan Origination System database.
- Compliance team will define audit retention requirements.
- QA team will validate functional and UAT test scenarios.

---

## 9. Dependencies

- Availability of business stakeholders for requirement review.
- Final approval of document checklist by compliance and operations teams.
- API availability from backend services.
- Development team availability for implementation.
- QA environment availability for testing.
- Test data availability for UAT.
- Product owner approval for backlog prioritization.

---

## 10. Business Requirements

| Requirement ID | Business Requirement | Priority |
|---|---|---|
| BR-001 | The system shall allow borrowers to register and log in securely. | High |
| BR-002 | The system shall allow borrowers to submit mortgage loan applications online. | High |
| BR-003 | The system shall capture borrower personal, employment, income, property, and loan details. | High |
| BR-004 | The system shall allow borrowers to upload required mortgage documents. | High |
| BR-005 | The system shall validate mandatory fields before application submission. | High |
| BR-006 | The system shall generate a unique loan application number after successful submission. | High |
| BR-007 | The system shall allow loan officers to review submitted applications. | High |
| BR-008 | The system shall allow loan officers to request missing information or move applications to underwriting. | High |
| BR-009 | The system shall allow underwriters to approve, reject, or request additional documents. | High |
| BR-010 | The system shall allow borrowers to track loan application status. | High |
| BR-011 | The system shall send automated email notifications when application status changes. | Medium |
| BR-012 | The system shall maintain audit history for all status updates and decisions. | High |
| BR-013 | The system shall provide managers with a loan pipeline dashboard. | Medium |
| BR-014 | The system shall allow internal users to search applications by borrower name, loan number, status, and submission date. | Medium |
| BR-015 | The system shall support role-based access for borrowers, loan officers, underwriters, managers, and compliance users. | High |

---

## 11. Business Rules

| Rule ID | Business Rule |
|---|---|
| BUS-001 | Borrower must complete all mandatory fields before submitting the loan application. |
| BUS-002 | Loan amount must be greater than zero. |
| BUS-003 | Annual income is mandatory for underwriting review. |
| BUS-004 | Uploaded documents must be in PDF, JPG, or PNG format. |
| BUS-005 | File size should not exceed 10 MB per document. |
| BUS-006 | Underwriter comments are mandatory when rejecting an application. |
| BUS-007 | Borrower must be notified when application status changes. |
| BUS-008 | Every status change must be captured in the audit trail. |
| BUS-009 | Loan officers cannot approve or reject loans. Only underwriters can make final decisions. |
| BUS-010 | Managers can view dashboards but cannot modify borrower application details. |

---

## 12. Risks

| Risk ID | Risk Description | Impact | Mitigation |
|---|---|---|---|
| R-001 | Delay in finalizing document checklist | High | Schedule early review with compliance and operations teams |
| R-002 | API delays from backend team | Medium | Track API dependencies during sprint planning |
| R-003 | UAT delays due to business user availability | Medium | Plan UAT schedule in advance |
| R-004 | Incomplete requirements for underwriting workflow | High | Conduct detailed requirement sessions with underwriters |
| R-005 | Dashboard data mismatch | Medium | Validate data mapping and SQL queries with reporting team |

---

## 13. Success Metrics

The project will be considered successful if:

- Borrowers can submit loan applications online without manual support.
- Required documents can be uploaded and tracked successfully.
- Loan officers can review and move applications to underwriting.
- Underwriters can complete approval, rejection, or document request decisions.
- Borrowers receive automated status notifications.
- Audit trail captures status changes accurately.
- Managers can view accurate loan pipeline dashboard data.
- UAT is completed with business sign-off.

---

## 14. Approval

| Name | Role | Approval Status |
|---|---|---|
| Product Owner | Business Owner | Pending |
| Operations Manager | Business Stakeholder | Pending |
| Compliance Lead | Compliance Reviewer | Pending |
| QA Lead | Testing Owner | Pending |
| Business Analyst | Document Owner | Drafted |