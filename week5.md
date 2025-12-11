# Week 5 – Advanced Security & Monitoring Infrastructure

## 1. Weekly Overview

**Focus of this week:**  
Strengthen the server’s security posture by enabling mandatory access control (MAC), configuring automatic security updates, setting up fail2ban to protect SSH, and creating scripts to:

- Check the security baseline on the server.
- Remotely monitor server performance from the workstation.

**Date range:** [dd/mm/yyyy – dd/mm/yyyy]

---

## 2. Weekly Objectives

By the end of this week, I aimed to:

1. Enable and verify a MAC framework (AppArmor or SELinux) on the server.
2. Configure automatic security updates so the server regularly receives security patches.
3. Install and configure fail2ban to defend against SSH brute-force attacks.
4. Write and test a `security-baseline.sh` script on the server to verify key security settings.
5. Write and test a `monitor-server.sh` script on the workstation to collect performance data via SSH.

---

## 3. Mandatory Access Control (MAC)

### 3.1 MAC Framework and Operating Mode

- **Chosen MAC framework:** [AppArmor / SELinux]  
- **Current mode:** [Enforcing / Permissive]  
- **Reason for this choice:**
  - [e.g. “AppArmor is the default on Ubuntu and easier to manage with pre-built profiles.”]
  - [e.g. “It integrates well with my chosen distribution and has good documentation.”]

### 3.2 Commands Used and Status Output

Commands (examples):

```bash
# AppArmor example:
sudo aa-status

# SELinux example:
sestatus
