# Functional Design Document: Rule-Based Lead Scoring

**Project:** Rule-Based Lead Scoring Accelerator
**Version:** 1.0
**Date:** 18/11/2025
**Author:** Mirza Zohaib Baig

---

## 1. Introduction

### 1.1 Project Purpose

This document details the functional design for the "Rule-Based Lead Scoring Accelerator" Proof of Concept (PoC) for Dynamics 365 Sales. This solution solves the business problem of inefficient lead prioritization by providing an automated, logic-driven scoring mechanism.

### 1.2 Business Problem

Sales teams struggle to prioritize leads effectively. High-potential leads are often overlooked while time is spent on poor-quality leads, resulting in lower conversion rates and lost revenue.

### 1.3 Business Objectives

- **Standardize Prioritization:** Eliminate subjective guessing by applying consistent business rules.
- **Increase Efficiency:** Automate the calculation so reps can focus on selling.
- **Improve Visibility:** Provide immediate visual indicators for high-quality leads.

### 1.4 Scope

- **In Scope:** D365 `Lead` entity customization, Power Automate flow for scoring logic, and D365 Form/View/Dashboard updates.
- **Out of Scope:** AI/Machine Learning models (Phase 2), Opportunity scoring.

---

## 2. Business Process Mapping

### 2.1 To-Be Process

1.  **Lead Created:** Salesperson or integration creates a new Lead.
2.  **Auto-Trigger:** Power Automate flow triggers immediately on creation.
3.  **Scoring Engine:** The flow evaluates the lead against the "Scoring Rules Matrix" (Budget, Source, Industry).
4.  **Update:** The flow calculates the total score and updates the `Lead Score` and `Score Rationale` fields in D365.
5.  **Prioritize:** High-score leads (>80) are flagged on the dashboard and forms.

---

## 3. Functional Solution Design (FSD)

### 3.1 Data Model (Entity Customization)

The following customizations have been made to the `Lead` entity:

| Display Name             | Logical Name         | Data Type        | Description                                  |
| :----------------------- | :------------------- | :--------------- | :------------------------------------------- |
| **Lead Score**           | `new_leadscore`      | Whole Number     | Calculated score (0-100).                    |
| **Score Rationale**      | `new_scorerationale` | Text (Multiline) | Explanation of how the score was calculated. |
| **Rule-Based Scored On** | `new_aiscoredon`     | Date and Time    | Timestamp of calculation.                    |

### 3.2 Scoring Rules Matrix (Power Automate Logic)

The scoring engine will apply the following weighted rules. The Base Score starts at **50**.

| Rule Condition                              | Points Added | Rationale Text          |
| :------------------------------------------ | :----------: | :---------------------- |
| **Budget Amount** > 50,000                  |     +30      | "High Budget (+30)"     |
| **Lead Source** is "Referral"               |     +20      | "Referral Source (+20)" |
| **Industry** is "Financial" or "Technology" |     +10      | "Target Industry (+10)" |

_Example:_ A Referral in the Tech industry with 60k budget = 50 + 30 + 20 + 10 = **110 (Capped at 100)**.

### 3.3 Form & View Customizations

- **Form:** A new "Scoring Insights" tab displays the score fields. `Score Rationale` is read-only.
- **Visuals:** A Business Rule displays a notification if Score > 80.

---

## 4. Security & Licensing

- **Security Roles:** Uses standard Sales roles. No special privileges required.
- **Licensing:** Fully functional with standard **Dynamics 365 Sales** and **Power Automate** licenses. No AI Builder credits required.
