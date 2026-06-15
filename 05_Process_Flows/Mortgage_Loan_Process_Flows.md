# Mortgage Loan Process Flows

## Project Name

Digital Mortgage Loan Origination & Applicant Tracking System

## Document Type

Business Process Flow Document

## Domain

Banking / Mortgage / Financial Services

---

## 1. Purpose

This document explains the major business process flows for the Mortgage Loan Origination System enhancement.

The process flows help business stakeholders, product owners, development teams, QA teams, and UAT users understand how borrowers, loan officers, underwriters, compliance users, and operations managers interact with the system.

---

## 2. High-Level End-to-End Mortgage Application Flow

```mermaid
flowchart TD
    A[Borrower Registers / Logs In] --> B[Starts Mortgage Application]
    B --> C[Enters Personal Details]
    C --> D[Enters Employment and Income Details]
    D --> E[Enters Property and Loan Details]
    E --> F[Uploads Required Documents]
    F --> G[Submits Application]
    G --> H[System Generates Application ID]
    H --> I[Loan Officer Reviews Application]
    I --> J{Application Complete?}
    J -->|No| K[Request Missing Documents]
    K --> L[Borrower Uploads Missing Documents]
    L --> I
    J -->|Yes| M[Move to Underwriting]
    M --> N[Underwriter Reviews Application]
    N --> O{Underwriter Decision}
    O -->|Approved| P[Application Approved]
    O -->|Rejected| Q[Application Rejected]
    O -->|More Info Needed| R[Request Additional Information]
    R --> S[Borrower Provides Additional Info]
    S --> N
    P --> T[Notify Borrower]
    Q --> T
    T --> U[Update Dashboard]
    U --> V[Capture Audit Trail]
```

---

## 3. Borrower Application Submission Flow

```mermaid
flowchart TD
    A[Borrower Logs In] --> B[Click New Loan Application]
    B --> C[Enter Personal Details]
    C --> D[Enter Employment Details]
    D --> E[Enter Income Details]
    E --> F[Enter Property Details]
    F --> G[Enter Loan Details]
    G --> H[Upload Required Documents]
    H --> I{All Mandatory Fields Completed?}
    I -->|No| J[Show Validation Errors]
    J --> C
    I -->|Yes| K[Submit Application]
    K --> L[Generate Application ID]
    L --> M[Set Status as Submitted]
    M --> N[Send Confirmation Email]
    N --> O[Display Application in Borrower Dashboard]
```

---

## 4. Document Upload Flow

```mermaid
flowchart TD
    A[Borrower Opens Document Upload Page] --> B[Select Document Type]
    B --> C[Choose File]
    C --> D{File Format Valid?}
    D -->|No| E[Show Unsupported File Error]
    E --> C
    D -->|Yes| F{File Size <= 10 MB?}
    F -->|No| G[Show File Size Error]
    G --> C
    F -->|Yes| H[Upload Document]
    H --> I[Set Document Status as Submitted]
    I --> J{All Required Documents Uploaded?}
    J -->|No| K[Show Pending Documents]
    J -->|Yes| L[Allow Application Submission]
```

---

## 5. Loan Officer Review Flow

```mermaid
flowchart TD
    A[Loan Officer Logs In] --> B[Open Submitted Applications Queue]
    B --> C[Select Application]
    C --> D[Review Borrower Details]
    D --> E[Review Employment and Income Details]
    E --> F[Review Property and Loan Details]
    F --> G[Review Uploaded Documents]
    G --> H{Application Complete?}
    H -->|No| I[Request Missing Documents]
    I --> J[Add Comments]
    J --> K[Update Status to Pending Documents]
    K --> L[Notify Borrower]
    L --> M[Capture Audit Trail]
    H -->|Yes| N[Move Application to Underwriting]
    N --> O[Update Status to Underwriting]
    O --> P[Notify Borrower]
    P --> Q[Capture Audit Trail]
```

---

## 6. Underwriter Decision Flow

```mermaid
flowchart TD
    A[Underwriter Logs In] --> B[Open Underwriting Queue]
    B --> C[Select Application]
    C --> D[Review Application Details]
    D --> E[Review Income and Employment]
    E --> F[Review Property and Loan Details]
    F --> G[Review Uploaded Documents]
    G --> H[Add Review Comments]
    H --> I{Decision}
    I -->|Approve| J[Approve Application]
    J --> K[Update Status to Approved]
    K --> L[Notify Borrower]
    L --> M[Update Manager Dashboard]
    M --> N[Capture Audit Trail]
    I -->|Reject| O[Enter Mandatory Rejection Comments]
    O --> P[Reject Application]
    P --> Q[Update Status to Rejected]
    Q --> R[Notify Borrower]
    R --> S[Update Manager Dashboard]
    S --> T[Capture Audit Trail]
    I -->|Need More Info| U[Request Additional Information]
    U --> V[Update Status to Additional Info Required]
    V --> W[Notify Borrower]
    W --> X[Capture Audit Trail]
```

---

## 7. Borrower Status Tracking Flow

```mermaid
flowchart TD
    A[Borrower Logs In] --> B[Open Application Dashboard]
    B --> C[View Submitted Applications]
    C --> D[Select Application]
    D --> E[View Current Status]
    E --> F[View Submitted Date and Application ID]
    F --> G{Action Required?}
    G -->|No| H[Continue Tracking Status]
    G -->|Yes| I[Upload Missing Documents or Additional Info]
    I --> J[System Updates Application]
    J --> K[Notify Internal User]
```

---

## 8. Notification Flow

```mermaid
flowchart TD
    A[Application Status Change Occurs] --> B[System Identifies New Status]
    B --> C{Notification Required?}
    C -->|No| D[No Email Sent]
    C -->|Yes| E[Generate Email Template]
    E --> F[Include Application ID and Status]
    F --> G[Send Email to Borrower]
    G --> H[Log Notification Event]
    H --> I[Capture Audit Trail]
```

---

## 9. Manager Dashboard Flow

```mermaid
flowchart TD
    A[Operations Manager Logs In] --> B[Open Loan Pipeline Dashboard]
    B --> C[System Fetches Application Data]
    C --> D[Display Total Applications]
    D --> E[Display Applications by Status]
    E --> F[Display Pending Documents]
    F --> G[Display Approved and Rejected Counts]
    G --> H[Display SLA Aging]
    H --> I{Filter Required?}
    I -->|Yes| J[Apply Date / Status Filter]
    J --> C
    I -->|No| K[View Dashboard Summary]
```

---

## 10. Audit Trail Flow

```mermaid
flowchart TD
    A[User Performs Action] --> B[System Identifies Action Type]
    B --> C[Capture Application ID]
    C --> D[Capture User ID and Role]
    D --> E[Capture Old Value]
    E --> F[Capture New Value]
    F --> G[Capture Timestamp]
    G --> H[Capture Comments if Available]
    H --> I[Save Audit Record]
    I --> J[Audit Trail Available for Compliance Review]
```

---

## 11. Key Status Transition Flow

| Current Status | Action | New Status | Performed By |
|---|---|---|---|
| Draft | Submit Application | Submitted | Borrower |
| Submitted | Start Review | In Review | Loan Officer |
| In Review | Request Missing Documents | Pending Documents | Loan Officer |
| Pending Documents | Upload Missing Documents | Submitted | Borrower |
| In Review | Move to Underwriting | Underwriting | Loan Officer |
| Underwriting | Approve Application | Approved | Underwriter |
| Underwriting | Reject Application | Rejected | Underwriter |
| Underwriting | Request More Info | Additional Info Required | Underwriter |
| Additional Info Required | Submit Additional Info | Underwriting | Borrower |
| Submitted | Withdraw Application | Withdrawn | Borrower |

---

## 12. BA Notes

As a Business Analyst, these process flows help in:

- Explaining current and future state workflows.
- Reviewing business logic with stakeholders.
- Helping developers understand expected system behavior.
- Helping QA teams design test scenarios.
- Identifying gaps in status transitions.
- Supporting UAT preparation.
- Maintaining requirement traceability.
