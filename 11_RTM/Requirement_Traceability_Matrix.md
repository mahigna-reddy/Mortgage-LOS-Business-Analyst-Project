# Requirement Traceability Matrix

## Project Name

Digital Mortgage Loan Origination & Applicant Tracking System

## Document Type

Requirement Traceability Matrix

## Domain

Banking / Mortgage / Financial Services

---

## 1. Purpose

This Requirement Traceability Matrix maps business requirements to functional requirements, user stories, API requirements, UAT test cases, and current coverage status.

The purpose of RTM is to ensure every business requirement is properly documented, developed, tested, and validated during UAT.

As a Business Analyst, this document helps maintain end-to-end requirement traceability from requirement gathering through final business sign-off.

---

## 2. Traceability Matrix

| Business Requirement ID | Business Requirement Description                                                                                         | Functional Requirement ID              | User Story ID                  | API ID                    | UAT Test Case ID                       | Status  |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------ | -------------------------------------- | ------------------------------ | ------------------------- | -------------------------------------- | ------- |
| BR-001                  | The system shall allow borrowers to register and log in securely.                                                        | FR-001, FR-002                         | US-001, US-002                 | API-001, API-002          | TC-001, TC-002, TC-003                 | Covered |
| BR-002                  | The system shall allow borrowers to submit mortgage loan applications online.                                            | FR-003                                 | US-003                         | API-003                   | TC-004, TC-006                         | Covered |
| BR-003                  | The system shall capture borrower personal, employment, income, property, and loan details.                              | FR-004, FR-005, FR-006, FR-007, FR-008 | US-004, US-005, US-006         | API-003                   | TC-004, TC-005                         | Covered |
| BR-004                  | The system shall allow borrowers to upload required mortgage documents.                                                  | FR-009                                 | US-007, US-008                 | API-005                   | TC-007, TC-008, TC-009                 | Covered |
| BR-005                  | The system shall validate mandatory fields before application submission.                                                | FR-010                                 | US-004, US-005, US-006         | API-003                   | TC-005                                 | Covered |
| BR-006                  | The system shall generate a unique loan application number after successful submission.                                  | FR-011                                 | US-003                         | API-003                   | TC-004                                 | Covered |
| BR-007                  | The system shall allow loan officers to review submitted applications.                                                   | FR-013, FR-014                         | US-009                         | API-004, API-008          | TC-010                                 | Covered |
| BR-008                  | The system shall allow loan officers to request missing information or move applications to underwriting.                | FR-015, FR-016                         | US-010, US-011                 | API-006, API-008          | TC-011, TC-012                         | Covered |
| BR-009                  | The system shall allow underwriters to approve, reject, or request additional documents.                                 | FR-017, FR-018, FR-019, FR-020         | US-012, US-013, US-014, US-015 | API-006, API-009          | TC-013, TC-014, TC-015, TC-016, TC-017 | Covered |
| BR-010                  | The system shall allow borrowers to track loan application status.                                                       | FR-012                                 | US-016                         | API-004, API-007          | TC-018                                 | Covered |
| BR-011                  | The system shall send automated email notifications when application status changes.                                     | FR-021                                 | US-017                         | API-006                   | TC-019                                 | Covered |
| BR-012                  | The system shall maintain audit history for all status updates and decisions.                                            | FR-022                                 | US-020                         | API-011                   | TC-021                                 | Covered |
| BR-013                  | The system shall provide managers with a loan pipeline dashboard.                                                        | FR-023                                 | US-018, US-019                 | API-010                   | TC-020                                 | Covered |
| BR-014                  | The system shall allow internal users to search applications by borrower name, loan number, status, and submission date. | FR-024                                 | US-021                         | API-004, API-008, API-009 | TC-022, TC-023                         | Covered |
| BR-015                  | The system shall support role-based access for borrowers, loan officers, underwriters, managers, and compliance users.   | FR-025                                 | US-001, US-002, US-020         | API-002                   | TC-024                                 | Covered |

---

## 3. Coverage Summary

| Coverage Area           | Total Count | Covered | Not Covered |
| ----------------------- | ----------: | ------: | ----------: |
| Business Requirements   |          15 |      15 |           0 |
| Functional Requirements |          25 |      25 |           0 |
| User Stories            |          21 |      21 |           0 |
| API Requirements        |          11 |      11 |           0 |
| UAT Test Cases          |          24 |      24 |           0 |

---

## 4. Requirement Priority Summary

| Priority | Requirement IDs                                                                                |
| -------- | ---------------------------------------------------------------------------------------------- |
| High     | BR-001, BR-002, BR-003, BR-004, BR-005, BR-006, BR-007, BR-008, BR-009, BR-010, BR-012, BR-015 |
| Medium   | BR-011, BR-013, BR-014                                                                         |
| Low      | None                                                                                           |

---

## 5. Traceability Notes

* Every business requirement is mapped to at least one functional requirement.
* Every high-priority business requirement has one or more UAT test cases.
* API requirements are mapped where system integration or backend validation is involved.
* Dashboard, audit, and notification requirements have specific UAT coverage.
* Role-based access is validated across borrower, loan officer, underwriter, manager, and compliance roles.

---

## 6. RTM Usage During Project

The RTM will be used during:

* Requirement review
* Sprint planning
* Backlog grooming
* Development clarification
* QA test planning
* UAT preparation
* Defect triage
* Business sign-off

---

## 7. BA Responsibilities

As a Business Analyst, RTM responsibilities include:

* Maintaining traceability between BRD, FRD, user stories, API requirements, and UAT test cases.
* Updating requirement status when scope changes.
* Ensuring all high-priority business requirements are tested.
* Supporting QA team in confirming test coverage.
* Supporting product owner and business stakeholders during UAT sign-off.
* Identifying gaps between requirements and test coverage.

---

## 8. Approval

| Name             | Role           | Approval Status |
| ---------------- | -------------- | --------------- |
| Product Owner    | Business Owner | Pending         |
| QA Lead          | Testing Owner  | Pending         |
| Business Analyst | Document Owner | Drafted         |
