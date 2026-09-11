# Lab Practice: Task 4 - Installing Security Templates via MMC

## 1. Task Overview & Objectives

The objective of this task is to configure, analyze, and apply standardized system security baselines using the Microsoft Management Console (MMC). Utilizing security templates allows administrators to automate and centralize administrative policies, user privilege assignments, registry permissions, and audit policies across Windows systems.

* **Target OS:** Windows Laboratory Host
* **Management Tool:** Microsoft Management Console (`mmc.exe`)
* **Key Snap-in:** Security Configuration and Analysis

---

## 2. Step-by-Step Task Execution & Evidence

### Task 4: Installing Security Templates via MMC

1. Launched the Microsoft Management Console by typing `MMC` in the Run prompt (`Win + R`).
2. Added the **Security Configuration and Analysis** snap-in via `Console > Add/Remove Snap-in` (or `File > Add/Remove Snap-in`).
3. Created a new security database, imported a hardened security template, and executed the security analysis against current system settings.
4. Reviewed configuration discrepancies and applied the template to enforce security baseline configurations.

> **📸 Verification Screenshot 4: MMC Security Configuration and Analysis Snap-in**
> ![MMC Security Template](./screenshots/task4_mmc_template.png)

---

## 3. Technical Analysis & Lab Questions

**Question: Why is using Security Templates and the MMC Security Configuration and Analysis snap-in beneficial for enterprise system hardening?**

* **Answer:** Security Templates provide a centralized, repeatable method to enforce consistent security policies (such as password policies, audit policies, and user rights assignments) across multiple hosts. The MMC Security Configuration and Analysis tool enables security personnel to perform baseline compliance auditing, identify security drift, and immediately remediate non-compliant settings without requiring manual registry edits across individual machines.


