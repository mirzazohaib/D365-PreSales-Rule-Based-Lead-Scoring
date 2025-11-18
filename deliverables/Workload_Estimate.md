# Workload Estimate: Rule-Based Lead Scoring PoC

**Project:** Rule-Based Lead Scoring Accelerator
**Date:** 18/11/2025

---

This document provides a Rough Order of Magnitude (ROM) estimate for the initial Proof of Concept (PoC) phase.

### **Phase 1: Proof of Concept (PoC)**

| Task                           | Role                  | Estimated Hours | Notes                                                                 |
| :----------------------------- | :-------------------- | :-------------: | :-------------------------------------------------------------------- |
| **1. Discovery & Design**      |                       |     **4.0**     |                                                                       |
| 1.1 Rules Workshop             | Functional Consultant |       2.0       | Define the "Scoring Matrix" (points for Budget, Industry, etc.).      |
| 1.2 Solution Design            | Functional Consultant |       2.0       | Create FDD and Field Mapping.                                         |
| **2. Configuration**           |                       |     **3.0**     |                                                                       |
| 2.1 D365 Customization         | Functional Consultant |       1.5       | Create `Lead` fields, "Scoring Insights" tab, and Views.              |
| 2.2 Data Prep                  | Data Analyst          |       1.5       | Create sample data to test positive/negative rules.                   |
| **3. Automation (The Engine)** |                       |     **4.0**     |                                                                       |
| 3.1 Power Automate Flow        | Functional Consultant |       3.0       | Build the logic: Triggers, Condition Branches, Calculation variables. |
| 3.2 Testing & Refinement       | Functional Consultant |       1.0       | Verify score calculations against test cases.                         |
| **4. Project Management**      |                       |     **1.0**     |                                                                       |
| 4.1 PM & Demo Prep             | Project Manager       |       1.0       | Status updates and final demo recording.                              |
| **Total Estimated Hours**      |                       |    **12.0**     |                                                                       |

---

### **Phase 2: Production Rollout (Estimate)**

A full rollout, including complex rule logic definition, UAT, and user training, is estimated at **40-60 hours**.
