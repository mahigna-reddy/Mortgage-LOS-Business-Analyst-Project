# Weekly Status Report

## Project Name

Digital Mortgage Loan Origination & Applicant Tracking System

## Document Type

Weekly Project Status Report

## Domain

Banking / Mortgage / Financial Services

---

## Reporting Week

Sprint 2, Week 1

## Overall Project Status

| Area            | Status      |
| --------------- | ----------- |
| Requirements    | On Track    |
| Development     | In Progress |
| QA Testing      | Not Started |
| UAT Preparation | In Progress |
| Risks           | Moderate    |
| Overall Status  | On Track    |

---

## 1. Executive Summary

The Mortgage Loan Origination System enhancement project is progressing as planned. The team completed requirement documentation for borrower application submission, document upload, loan officer review, underwriting workflow, status tracking, and dashboard reporting.

The Business Analyst team worked closely with product owners, loan officers, underwriters, compliance users, development team, and QA team to clarify business rules, user stories, API expectations, and UAT scenarios.

The current focus is on finalizing underwriting decision workflow, dashboard reporting requirements, API validation rules, and UAT preparation.

---

## 2. Completed This Week

| Item               | Description                                                                          | Owner   | Status    |
| ------------------ | ------------------------------------------------------------------------------------ | ------- | --------- |
| Requirement Review | Reviewed borrower application workflow with product owner                            | BA      | Completed |
| User Stories       | Created user stories and acceptance criteria for Sprint 1 and Sprint 2               | BA      | Completed |
| BRD Updates        | Updated business requirements based on stakeholder feedback                          | BA      | Completed |
| FRD Updates        | Added validation rules, notification rules, and audit requirements                   | BA      | Completed |
| API Requirements   | Documented API requirements for loan application, document upload, and status update | BA      | Completed |
| Process Flows      | Created process flows for borrower, loan officer, and underwriter workflows          | BA      | Completed |
| Data Mapping       | Drafted source-to-target mapping for borrower, loan, document, and dashboard data    | BA      | Completed |
| UAT Scenarios      | Created initial UAT scenarios for business validation                                | BA / QA | Completed |

---

## 3. In Progress

| Item                         | Description                                                                        | Owner                   | Target Date | Status      |
| ---------------------------- | ---------------------------------------------------------------------------------- | ----------------------- | ----------- | ----------- |
| Underwriting Workflow Review | Final review with underwriting team for approval/rejection/additional info process | BA / Underwriting Team  | End of Week | In Progress |
| Dashboard Metrics            | Finalizing dashboard fields and filter criteria                                    | BA / Operations Manager | End of Week | In Progress |
| API Error Scenarios          | Reviewing API error handling with technical lead                                   | BA / Tech Lead          | Next Week   | In Progress |
| UAT Test Case Review         | Reviewing UAT test cases with QA and business users                                | BA / QA                 | Next Week   | In Progress |
| RTM Update                   | Mapping latest requirements to user stories and UAT test cases                     | BA                      | Ongoing     | In Progress |

---

## 4. Planned for Next Week

| Item                            | Description                                                 | Owner                   |
| ------------------------------- | ----------------------------------------------------------- | ----------------------- |
| Finalize Dashboard Requirements | Confirm dashboard metrics, filters, and export requirements | BA / Operations Manager |
| Review API Requirements         | Walkthrough API requirements with development and QA teams  | BA / Tech Lead / QA     |
| UAT Walkthrough                 | Review UAT test cases with business users                   | BA / Business Users     |
| Defect Triage Process           | Define defect triage process for UAT cycle                  | BA / QA Lead            |
| Finalize RTM                    | Ensure all business requirements are mapped to test cases   | BA                      |
| Sprint Review Support           | Support product owner during sprint review                  | BA                      |

---

## 5. Key Decisions Made

| Decision ID | Decision                                                       | Impact                                      |
| ----------- | -------------------------------------------------------------- | ------------------------------------------- |
| DEC-001     | Borrower can save application as Draft before final submission | Improves borrower experience                |
| DEC-002     | Borrower cannot edit application after final submission        | Protects data integrity                     |
| DEC-003     | Loan officer cannot approve or reject applications             | Maintains proper role separation            |
| DEC-004     | Rejection comments are mandatory for underwriters              | Supports compliance and audit               |
| DEC-005     | Dashboard will include SLA aging report                        | Helps management track delayed applications |
| DEC-006     | Audit trail will capture all status changes and decisions      | Supports compliance requirements            |

---

## 6. Open Questions

| Question ID | Open Question                                                    | Owner              | Target Resolution |
| ----------- | ---------------------------------------------------------------- | ------------------ | ----------------- |
| Q-001       | What is the final list of mandatory mortgage documents?          | Compliance Team    | This Week         |
| Q-002       | What is the SLA threshold for application aging?                 | Operations Manager | This Week         |
| Q-003       | Should borrowers receive SMS notifications in addition to email? | Product Owner      | Next Week         |
| Q-004       | What dashboard filters are mandatory for Phase 1?                | Operations Manager | This Week         |
| Q-005       | How long should audit records be retained?                       | Compliance Team    | Next Week         |

---

## 7. Risks and Issues

| Risk ID | Risk / Issue                                           | Impact | Mitigation                                     | Status      |
| ------- | ------------------------------------------------------ | ------ | ---------------------------------------------- | ----------- |
| R-001   | Delay in finalizing mandatory document checklist       | High   | Schedule follow-up with compliance team        | Open        |
| R-002   | Underwriting workflow has multiple exception scenarios | High   | Conduct detailed walkthrough with underwriters | Open        |
| R-003   | Dashboard calculations may not match backend data      | Medium | Validate with SQL queries and reporting team   | Open        |
| R-004   | Business users may have limited availability for UAT   | Medium | Schedule UAT sessions in advance               | Open        |
| R-005   | API error scenarios may need additional clarification  | Medium | Review with technical lead and QA team         | In Progress |

---

## 8. Milestone Status

| Milestone              | Target Date | Status      |
| ---------------------- | ----------- | ----------- |
| BRD Completion         | Sprint 1    | Completed   |
| FRD Completion         | Sprint 1    | Completed   |
| User Stories Ready     | Sprint 1    | Completed   |
| API Requirements Draft | Sprint 2    | Completed   |
| Data Mapping Draft     | Sprint 2    | Completed   |
| UAT Test Cases Draft   | Sprint 2    | Completed   |
| UAT Review             | Sprint 3    | Not Started |
| Business Sign-Off      | Sprint 3    | Not Started |

---

## 9. BA Activities This Week

As the Business Analyst, the following activities were completed:

* Conducted requirement clarification sessions with product owner and business stakeholders.
* Updated BRD and FRD based on latest business feedback.
* Created detailed user stories with acceptance criteria.
* Documented process flows for borrower, loan officer, and underwriter workflows.
* Created API requirements for loan application, document upload, status update, and dashboard.
* Prepared UAT test cases for borrower and internal user workflows.
* Updated RTM to maintain requirement-to-test coverage.
* Supported QA team with business rule clarification.
* Identified open questions and risks for stakeholder follow-up.

---

## 10. Status Color Legend

| Status | Meaning                   |
| ------ | ------------------------- |
| Green  | On Track                  |
| Yellow | At Risk / Needs Attention |
| Red    | Blocked or Delayed        |

---

## 11. Final Comments

The project remains on track. Main attention areas are finalizing compliance document requirements, confirming underwriting exception rules, and validating dashboard metrics. No major blockers have been identified at this time.
