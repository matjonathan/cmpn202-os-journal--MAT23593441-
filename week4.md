
---

## Week 5 – `week5.md`

```markdown
# Week 5 – Advanced Security & Monitoring Infrastructure

## 1. Weekly Overview

**Focus of this week:**  
Enhance security using MAC (SELinux/AppArmor), automatic updates, fail2ban, and write scripts for security baselines and monitoring.

**Date range:** [dd/mm/yyyy – dd/mm/yyyy]

---

## 2. Weekly Objectives

1. Enable and configure SELinux/AppArmor (depending on distro).
2. Configure automatic security updates.
3. Install and configure fail2ban to protect SSH.
4. Implement and test `security-baseline.sh` (server) and `monitor-server.sh` (workstation).

---

## 3. Mandatory Access Control (MAC)

### 3.1 Choice and Mode

- MAC framework: [SELinux / AppArmor]
- Mode: [Enforcing / Permissive]
- Reason for this choice: [e.g. supported by distro, easier to configure, etc.]

### 3.2 Commands & Status

```bash
# Example for AppArmor
sudo aa-status

# Example for SELinux
sestatus

