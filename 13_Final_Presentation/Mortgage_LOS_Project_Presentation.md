# Mortgage LOS Project Presentation

## Project Name

Digital Mortgage Loan Origination & Applicant Tracking System

## Domain

Banking / Mortgage / Financial Services

---

# Slide 1: Project Title

## Digital Mortgage Loan Origination & Applicant Tracking System

**Role:** Business Analyst
**Domain:** Banking / Mortgage / Financial Services
**Project Type:** Web Application Enhancement + API Integration + Workflow Automation
**Experience Level:** 5+ Years

---

# Slide 2: Project Overview

The project focused on enhancing an existing Mortgage Loan Origination System to improve the borrower application experience and internal loan review workflow.

The enhanced system allows borrowers to submit mortgage applications online, upload required documents, track loan status, and receive automated notifications.

Internal teams such as loan officers, underwriters, compliance users, and operations managers can review applications, update statuses, track audit history, and monitor loan pipeline reports.

---

# Slide 3: Business Problem

The existing mortgage application process had several manual steps and limited visibility.

## Key Problems

* Borrowers had limited visibility into loan application status.
* Loan officers manually followed up for missing documents.
* Underwriters did not have a centralized application review workflow.
* Application status updates were delayed.
* Managers lacked real-time loan pipeline reporting.
* Audit trail was not consistent for compliance tracking.
* Reporting required manual data extraction and spreadsheet updates.

---

# Slide 4: Business Objectives

## Main Objectives

* Enable borrowers to submit mortgage applications online.
* Allow borrowers to upload required mortgage documents.
* Provide real-time loan application status tracking.
* Allow loan officers to review applications and request missing documents.
* Allow underwriters to approve, reject, or request additional information.
* Send automated email notifications for status changes.
* Maintain audit trail for compliance.
* Provide dashboard reports for operations managers.

---

# Slide 5: Stakeholders

| Stakeholder        | Responsibility                                        |
| ------------------ | ----------------------------------------------------- |
| Borrower           | Submits mortgage application and uploads documents    |
| Loan Officer       | Reviews application completeness and borrower details |
| Underwriter        | Reviews loan risk and makes decision                  |
| Compliance Team    | Reviews audit and regulatory requirements             |
| Operations Manager | Monitors loan pipeline and SLA metrics                |
| Product Owner      | Owns business priorities and backlog                  |
| Business Analyst   | Documents requirements, process flows, UAT, RTM       |
| Development Team   | Builds application features and APIs                  |
| QA Team            | Tests functional, API, regression, and UAT scenarios  |

---

# Slide 6: Scope

## In Scope

* Borrower registration and login
* Mortgage loan application submission
* Employment, income, property, and loan details capture
* Required document upload
* Loan officer review workflow
* Underwriter decision workflow
* Borrower status tracking
* Automated notifications
* Audit trail
* Manager dashboard
* API requirements
* Data mapping
* UAT test cases
* Requirement traceability matrix

## Out of Scope

* Credit bureau integration
* Payment processing
* Loan closing document generation
* Mobile application development
* AI-based underwriting
* Third-party title or appraisal vendor integration

---

# Slide 7: Current State vs Future State

| Current State                                 | Future State                       |
| --------------------------------------------- | ---------------------------------- |
| Manual loan application follow-ups            | Online application submission      |
| Documents tracked through emails/spreadsheets | Centralized document upload        |
| Limited borrower status visibility            | Real-time borrower status tracking |
| Manual status updates                         | Automated status workflow          |
| Limited dashboard reporting                   | Loan pipeline dashboard            |
| Weak audit tracking                           | Complete audit trail               |
| Manual UAT validation                         | Requirement-based UAT coverage     |

---

# Slide 8: High-Level Process Flow

## End-to-End Mortgage Application Flow

1. Borrower registers or logs in.
2. Borrower starts mortgage loan application.
3. Borrower enters personal, employment, income, property, and loan details.
4. Borrower uploads required documents.
5. Borrower submits application.
6. System generates application ID.
7. Loan officer reviews application.
8. Loan officer requests missing documents or moves application to underwriting.
9. Underwriter reviews application.
10. Underwriter approves, rejects, or requests additional information.
11. System notifies borrower.
12. Dashboard and audit trail are updated.

---

# Slide 9: Key Business Requirements

| Requirement ID | Requirement                                                     |
| -------------- | --------------------------------------------------------------- |
| BR-001         | Borrower registration and secure login                          |
| BR-002         | Online mortgage loan application submission                     |
| BR-004         | Required document upload                                        |
| BR-007         | Loan officer application review                                 |
| BR-009         | Underwriter approval, rejection, or additional document request |
| BR-010         | Borrower application status tracking                            |
| BR-011         | Automated email notifications                                   |
| BR-012         | Audit history for status updates and decisions                  |
| BR-013         | Loan pipeline dashboard                                         |
| BR-015         | Role-based access control                                       |

---

# Slide 10: Functional Features

## Borrower Features

* Register and log in
* Create mortgage application
* Save application as draft
* Submit final application
* Upload documents
* Track application status
* Receive status notifications

## Internal User Features

* Loan officer review dashboard
* Missing document request
* Move application to underwriting
* Underwriter decision workflow
* Manager dashboard
* Audit trail search
* Role-based access

---

# Slide 11: User Stories

## Sample User Story 1

**As a** borrower,
**I want to** submit a mortgage loan application online,
**So that** I can apply for a home loan without visiting a branch.

## Acceptance Criteria

* Borrower can enter required personal, income, employment, property, and loan details.
* Mandatory fields are validated.
* Application ID is generated after successful submission.
* Application status is set to Submitted.
* Borrower receives confirmation notification.

---

# Slide 12: Wireframes Covered

The project included wireframe requirements for the following screens:

* Borrower Registration Page
* Borrower Login Page
* Borrower Dashboard
* Mortgage Application Form
* Document Upload Page
* Application Status Tracking Page
* Loan Officer Review Dashboard
* Loan Officer Application Review Page
* Underwriter Queue Page
* Underwriter Decision Page
* Operations Manager Dashboard
* Audit Trail Page

---

# Slide 13: API Requirements

## Key APIs Documented

| API ID  | API Name                      | Method |
| ------- | ----------------------------- | ------ |
| API-001 | Borrower Registration API     | POST   |
| API-002 | Borrower Login API            | POST   |
| API-003 | Create Loan Application API   | POST   |
| API-004 | Get Loan Application API      | GET    |
| API-005 | Upload Document API           | POST   |
| API-006 | Update Application Status API | PUT    |
| API-010 | Get Manager Dashboard API     | GET    |
| API-011 | Get Audit Trail API           | GET    |

## BA Contribution

* Documented request and response fields.
* Defined business rules.
* Captured error scenarios.
* Clarified API behavior with development and QA teams.
* Supported Postman and Swagger review discussions.

---

# Slide 14: Data Mapping

## Data Mapping Areas

* Borrower registration data
* Loan application data
* Document upload data
* Application status data
* Dashboard reporting data
* Notification data
* Audit trail data

## Purpose

The data mapping document helped ensure that data captured from the borrower portal was correctly stored in the LOS database, passed to underwriting systems, displayed on dashboards, and captured in audit logs.

---

# Slide 15: SQL Validation

SQL queries were used to support data validation, reporting verification, and UAT.

## Sample Validation Areas

* Borrower profile validation
* Loan application submission validation
* Document upload validation
* Application status validation
* Underwriting queue validation
* Dashboard count validation
* Audit trail validation
* Notification validation
* Data quality checks

---

# Slide 16: UAT Approach

## UAT Scope

* Borrower registration and login
* Mortgage application submission
* Document upload
* Loan officer review
* Missing document request
* Underwriter decision workflow
* Borrower status tracking
* Email notifications
* Manager dashboard
* Audit trail
* Role-based access

## UAT Goal

To confirm that the system meets business requirements and supports real business workflows before production release.

---

# Slide 17: RTM Coverage

The Requirement Traceability Matrix mapped:

* Business requirements
* Functional requirements
* User stories
* API requirements
* UAT test cases
* Coverage status

## Coverage Summary

| Area                    | Covered |
| ----------------------- | ------: |
| Business Requirements   | 15 / 15 |
| Functional Requirements | 25 / 25 |
| User Stories            | 21 / 21 |
| API Requirements        | 11 / 11 |
| UAT Test Cases          | 24 / 24 |

---

# Slide 18: Risks and Mitigation

| Risk                                       | Impact | Mitigation                                     |
| ------------------------------------------ | ------ | ---------------------------------------------- |
| Delay in finalizing document checklist     | High   | Schedule review with compliance team           |
| Underwriting workflow complexity           | High   | Conduct detailed walkthrough with underwriters |
| Dashboard data mismatch                    | Medium | Validate using SQL queries                     |
| Limited business user availability for UAT | Medium | Plan UAT schedule early                        |
| API error scenario gaps                    | Medium | Review with technical lead and QA              |

---

# Slide 19: BA Responsibilities

As a Business Analyst, responsibilities included:

* Requirement gathering with business stakeholders.
* Created BRD and FRD.
* Created user stories and acceptance criteria.
* Documented process flows and wireframe requirements.
* Created API requirements and data mapping documents.
* Prepared SQL validation queries.
* Created UAT test cases.
* Maintained RTM.
* Supported sprint planning, backlog grooming, and sprint reviews.
* Supported QA and UAT defect triage.
* Coordinated with product owner, developers, QA, compliance, loan officers, and underwriters.

---

# Slide 20: Business Impact

## Expected Benefits

* Reduced manual follow-ups between borrowers and loan officers.
* Improved borrower experience through online status tracking.
* Faster document review and underwriting workflow.
* Better visibility into loan application pipeline.
* Improved compliance through audit trail.
* Reduced application processing delays.
* Better reporting for operations managers.
* Improved requirement traceability and UAT coverage.

---

# Slide 21: Interview Explanation

One of my recent projects was a Mortgage Loan Origination System enhancement. The goal was to improve the digital mortgage application process for borrowers and internal teams such as loan officers, underwriters, compliance, and operations.

As a Business Analyst, I worked on gathering requirements, documenting BRD and FRD, creating user stories with acceptance criteria, preparing process flows, wireframe requirements, API requirements, data mapping, SQL validation queries, UAT test cases, and RTM.

The major enhancement areas were online loan application submission, document upload, underwriting decision workflow, borrower status tracking, automated notifications, audit trail, and manager dashboard reporting.

I worked closely with product owners, loan officers, underwriters, QA, developers, and compliance teams to clarify requirements, validate business rules, and support UAT sign-off.

---

# Slide 22: Project Artifacts

The project repository includes:

* Project Overview
* Business Requirements Document
* Functional Requirements Document
* User Stories and Acceptance Criteria
* Process Flows
* Wireframes
* API Requirements Document
* Data Mapping Document
* SQL Queries
* UAT Test Cases
* Requirement Traceability Matrix
* Weekly Status Report
* Final Presentation

---

# Slide 23: Final Summary

This project demonstrates end-to-end Business Analyst responsibilities for a 5+ year BA profile in the banking and mortgage domain.

It covers requirement gathering, business analysis, functional documentation, Agile user stories, API understanding, data mapping, SQL validation, UAT preparation, RTM, stakeholder communication, and project reporting.
