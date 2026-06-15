# Mortgage-LOS-Business-Analyst-Project
Business Analyst portfolio project for a Mortgage Loan Origination System covering BRD, FRD, user stories, process flows, wireframes, API requirements, data mapping, UAT test cases, RTM, and status reporting.

# Mortgage LOS Business Analyst Project

## Project Title

Digital Mortgage Loan Origination & Applicant Tracking System

## Project Overview

This is a Business Analyst portfolio project based on a Mortgage Loan Origination System enhancement in the banking, mortgage, and financial services domain.

The project demonstrates end-to-end Business Analyst responsibilities for a 5+ year experienced BA profile, including requirement gathering, BRD, FRD, user stories, process flows, wireframes, API requirements, data mapping, SQL validation, UAT test cases, RTM, stakeholder communication, and project status reporting.

The main goal of this project is to improve the digital mortgage loan application process by allowing borrowers to submit applications online, upload required documents, track application status, and receive automated notifications. Internal users such as loan officers, underwriters, compliance teams, and operations managers can review applications, update statuses, make underwriting decisions, track audit history, and monitor loan pipeline dashboards.

---

## Domain

Banking / Mortgage / Financial Services

---

## Project Type

Web Application Enhancement + API Integration + Workflow Automation

---

## Business Problem

The existing mortgage loan application process includes multiple manual steps and limited visibility for borrowers and internal teams.

Key problems identified:

* Borrowers have limited visibility into loan application status.
* Loan officers manually follow up for missing documents.
* Underwriters do not have a centralized review workflow.
* Application status updates are delayed.
* Operations managers lack real-time loan pipeline visibility.
* Compliance teams need better audit traceability.
* Reporting requires manual data extraction and spreadsheet updates.

---

## Business Objectives

The objective of this project is to improve the mortgage loan application and review process through a digital, trackable, and compliant workflow.

Business objectives include:

* Enable borrowers to submit mortgage applications online.
* Allow borrowers to upload required mortgage documents.
* Provide real-time loan application status tracking.
* Allow loan officers to review applications and request missing documents.
* Allow underwriters to approve, reject, or request additional information.
* Send automated email notifications when application status changes.
* Maintain audit history for compliance.
* Provide loan pipeline dashboard reports for operations managers.

---

## Key Features

* Borrower registration and secure login
* Online mortgage loan application submission
* Employment, income, property, and loan detail capture
* Required mortgage document upload
* Loan officer review workflow
* Underwriter decision workflow
* Borrower application status tracking
* Automated email notifications
* Application audit trail
* Manager loan pipeline dashboard
* Search and filter functionality
* Role-based access control
* API requirement documentation
* Data mapping documentation
* SQL validation queries
* UAT test cases
* Requirement Traceability Matrix

---

## Stakeholders

| Stakeholder        | Responsibility                                                      |
| ------------------ | ------------------------------------------------------------------- |
| Borrower           | Submits loan application and uploads required documents             |
| Loan Officer       | Reviews borrower information and validates application completeness |
| Underwriter        | Reviews loan risk, documents, income, and makes loan decision       |
| Compliance Team    | Ensures audit and regulatory requirements are met                   |
| Operations Manager | Tracks loan pipeline, SLA, pending applications, and approvals      |
| Product Owner      | Owns business priorities and backlog                                |
| Business Analyst   | Gathers requirements, documents workflows, supports UAT             |
| Development Team   | Builds application features and API integrations                    |
| QA Team            | Tests functional, API, regression, and UAT scenarios                |

---

## Tools Used

* Jira
* Confluence
* Microsoft Word
* Microsoft Excel
* Microsoft Visio / Draw.io
* SQL
* Postman
* Swagger
* PowerPoint
* GitHub

---

## Project Artifacts

| Folder                | Artifact                             | Description                                                                                                                  |
| --------------------- | ------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------- |
| 01_Project_Overview   | Project Overview                     | Project summary, business problem, objectives, scope, stakeholders, and BA responsibilities                                  |
| 02_BRD                | Business Requirements Document       | High-level business requirements, scope, assumptions, risks, success metrics, and approvals                                  |
| 03_FRD                | Functional Requirements Document     | Functional requirements, user roles, validation rules, notification rules, reporting, security, and audit requirements       |
| 04_User_Stories       | User Stories and Acceptance Criteria | Agile user stories grouped by epics with detailed acceptance criteria                                                        |
| 05_Process_Flows      | Mortgage Loan Process Flows          | Business process flows for borrower, loan officer, underwriter, notification, dashboard, and audit workflows                 |
| 06_Wireframes         | Wireframes                           | Screen-level wireframe requirements with fields, buttons, validations, and business rules                                    |
| 07_API_Requirements   | API Requirements Document            | API scope, endpoints, request/response examples, business rules, and error scenarios                                         |
| 08_Data_Mapping       | Data Mapping Document                | Source-to-target data mapping across borrower portal, LOS database, underwriting, dashboard, notification, and audit systems |
| 09_SQL_Queries        | SQL Queries                          | SQL queries for data validation, dashboard verification, UAT support, and defect analysis                                    |
| 10_UAT_Test_Cases     | UAT Test Cases                       | Business-facing UAT scenarios for borrower, loan officer, underwriter, manager, and compliance workflows                     |
| 11_RTM                | Requirement Traceability Matrix      | Mapping between business requirements, functional requirements, user stories, APIs, and UAT test cases                       |
| 12_Status_Reports     | Weekly Status Report                 | Sample project status report with completed work, in-progress items, risks, decisions, and next steps                        |
| 13_Final_Presentation | Final Presentation                   | Project presentation outline for interview and portfolio explanation                                                         |

---

## BA Responsibilities Demonstrated

This project demonstrates the following Business Analyst responsibilities:

* Requirement gathering with business stakeholders
* BRD and FRD documentation
* Current state and future state analysis
* User story creation
* Acceptance criteria writing
* Business process flow documentation
* Wireframe requirement preparation
* API requirement documentation
* Data mapping
* SQL-based data validation
* UAT test case preparation
* Requirement Traceability Matrix maintenance
* Stakeholder communication
* Sprint planning and backlog grooming support
* QA and UAT support
* Defect triage support
* Risk and issue tracking
* Weekly status reporting

---

## Sample Business Requirements

| Requirement ID | Requirement                                                                                                            |
| -------------- | ---------------------------------------------------------------------------------------------------------------------- |
| BR-001         | The system shall allow borrowers to register and log in securely.                                                      |
| BR-002         | The system shall allow borrowers to submit mortgage loan applications online.                                          |
| BR-004         | The system shall allow borrowers to upload required mortgage documents.                                                |
| BR-007         | The system shall allow loan officers to review submitted applications.                                                 |
| BR-009         | The system shall allow underwriters to approve, reject, or request additional documents.                               |
| BR-010         | The system shall allow borrowers to track loan application status.                                                     |
| BR-011         | The system shall send automated email notifications when application status changes.                                   |
| BR-012         | The system shall maintain audit history for all status updates and decisions.                                          |
| BR-013         | The system shall provide managers with a loan pipeline dashboard.                                                      |
| BR-015         | The system shall support role-based access for borrowers, loan officers, underwriters, managers, and compliance users. |

---

## Sample User Story

**As a** borrower,
**I want to** submit a mortgage loan application online,
**So that** I can apply for a home loan without visiting a branch.

### Acceptance Criteria

* Borrower can enter personal, employment, income, property, and loan details.
* Mandatory fields are validated.
* Application ID is generated after successful submission.
* Application status is set to Submitted.
* Borrower receives confirmation notification.
* Submitted application appears in borrower dashboard.

---

## API Requirements Covered

| API ID  | API Name                      | Method |
| ------- | ----------------------------- | ------ |
| API-001 | Borrower Registration API     | POST   |
| API-002 | Borrower Login API            | POST   |
| API-003 | Create Loan Application API   | POST   |
| API-004 | Get Loan Application API      | GET    |
| API-005 | Upload Document API           | POST   |
| API-006 | Update Application Status API | PUT    |
| API-007 | Get Borrower Applications API | GET    |
| API-008 | Get Loan Officer Queue API    | GET    |
| API-009 | Get Underwriter Queue API     | GET    |
| API-010 | Get Manager Dashboard API     | GET    |
| API-011 | Get Audit Trail API           | GET    |

---

## UAT Coverage

UAT test cases cover the following areas:

* Borrower registration
* Borrower login
* Invalid login validation
* Mortgage loan application submission
* Mandatory field validation
* Save as draft
* Document upload
* Unsupported document format validation
* File size validation
* Loan officer application review
* Missing document request
* Move to underwriting
* Underwriter review
* Loan approval
* Loan rejection
* Mandatory rejection comments
* Additional information request
* Borrower status tracking
* Email notifications
* Operations manager dashboard
* Audit trail
* Search and filter
* Role-based access

---

## RTM Coverage Summary

| Area                    | Covered |
| ----------------------- | ------: |
| Business Requirements   | 15 / 15 |
| Functional Requirements | 25 / 25 |
| User Stories            | 21 / 21 |
| API Requirements        | 11 / 11 |
| UAT Test Cases          | 24 / 24 |

---

## Expected Business Benefits

* Reduced manual follow-ups between borrowers and loan officers
* Improved borrower experience through online status tracking
* Faster document review and underwriting workflow
* Better loan pipeline visibility for operations managers
* Improved compliance through audit trail
* Reduced application processing delays
* Improved reporting accuracy
* Stronger requirement traceability and UAT coverage

---

