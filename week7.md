# Week 7 – Security Audit & System Evaluation

## 1. Weekly Overview

**Focus of this week:**  
Carry out a final security audit of the server, verify that all security controls implemented in previous weeks are working as intended, evaluate the overall system (security and performance), and reflect on the full seven-week Operating Systems project.

**Date range:** [dd/mm/yyyy – dd/mm/yyyy]

---

## 2. Weekly Objectives

By the end of this week, I aimed to:

1. Perform a system-wide security audit using Lynis.
2. Conduct a network security scan using nmap from the workstation.
3. Review all running services and justify which ones are enabled.
4. Verify that SSH hardening, firewall rules, MAC, fail2ban, and automatic updates are functioning correctly.
5. Identify any remaining risks and document possible future mitigations.
6. Provide a final evaluation and reflection on the completed system.

---

## 3. Lynis Security Audit

### 3.1 Running the Audit

I ran the Lynis security audit on the server with the following command:

```bash
sudo lynis audit system
