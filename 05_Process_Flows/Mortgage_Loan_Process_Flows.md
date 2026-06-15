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

The process flows help business stakeholders, development teams, QA teams, and product owners understand how borrowers, loan officers, underwriters, compliance users, and operations managers interact with the system.

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