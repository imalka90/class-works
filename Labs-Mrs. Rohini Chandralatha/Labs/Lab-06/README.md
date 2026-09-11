# Lab Practice: Task 6 - Patching Windows

## 1. Task Overview & Objectives

The objective of this task is to perform baseline patch management on a laboratory Windows machine. By connecting to update services, scanning for missing security rollups, installing system updates, and verifying applied Knowledge Base (KB) patches, the system's attack surface is minimized against known public vulnerabilities and exploits.

* **Target OS:** Windows Laboratory Host
* **Management Tool:** Windows Update / Installed Updates History (`wmic qfe` or Control Panel)
* **Primary Source:** Microsoft Update Services (`www.microsoft.com`)

---

## 2. Step-by-Step Task Execution & Evidence

### Task 6: Patching Windows

1. Navigated to Microsoft Update services (`www.microsoft.com`) or launched the Windows Update control panel to initiate a system vulnerability scan.
2. Identified critical missing security rollups, service packs, and software security patches.
3. Downloaded and installed available updates, restarting the system when required.
4. Verified and documented the list of successfully applied KB patches for security audit compliance.

> **📸 Verification Screenshot 6: System Patch Verification and Update Log**
> ![Windows Patch Log](./screenshots/task6_patch_log.png)

---

## 3. Technical Analysis & Lab Questions

**Question: Why is regular patch management critical for operating system security and risk mitigation?**

* **Answer:** Security patches address publicly disclosed vulnerabilities, zero-day exploits, and software bugs within the operating system. Unpatched systems remain highly susceptible to automated network worms, remote code execution (RCE) exploits, and privilege escalation attacks. Maintaining an up-to-date patch cycle ensures known security flaws are remediated before attackers can leverage them.

---

