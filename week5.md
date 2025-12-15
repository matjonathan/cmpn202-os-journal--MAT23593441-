## Week 5 – Advanced Security and Monitoring Infrastructure

---

## 1. Weekly Overview

**Focus of this week:**  
Strengthening the server’s security posture by enabling mandatory access control (MAC), configuring automatic security updates, setting up fail2ban to protect SSH, and creating scripts to verify the security baseline and remotely monitor server performance from the workstation.

---

## 2. Weekly Objectives

By the end of this week, I aimed to:

- Enable and verify a mandatory access control (MAC) framework on the server.
- Configure automatic security updates so the server regularly receives security patches.
- Install and configure fail2ban to defend against SSH brute-force attacks.
- Create and test a `security-baseline.sh` script on the server to verify key security settings.
- Create and test a `monitor-server.sh` script on the workstation to collect performance data via SSH.

---

## 3. Mandatory Access Control (MAC)

### 3.1 MAC Framework and Operating Mode

**Chosen MAC framework:** AppArmor  
**Current mode:** Enforcing

**Reason for this choice:**  
AppArmor is enabled by default on Ubuntu Server and integrates well with the distribution. It provides application-level confinement using human-readable profiles, making it easier to manage and audit compared to SELinux in smaller server environments. Its documentation and tooling are well suited for this coursework.

---

### 3.2 Commands Used and Status Output

sudo aa-status

**AppArmor status**

<img width="1263" height="668" alt="aa status" src="https://github.com/user-attachments/assets/f3a67563-d550-46cb-982f-ad3a6a0d9692" />



---

## 4. Automatic Security Updates

Automatic security updates were configured to ensure that critical security patches are applied without manual intervention.

**Commands executed (on server via SSH):**


To verify that AppArmor is enabled and enforcing profiles, the following command was executed on the server via SSH:


sudo apt update
sudo apt install unattended-upgrades
sudo dpkg-reconfigure --priority=low unattended-upgrades


---

## 5. Fail2ban – Intrusion and Brute-Force Protection

Fail2ban was installed and configured to monitor SSH authentication logs and automatically block IP addresses that exhibit repeated failed login attempts.

**Commands executed (on server via SSH):**


sudo apt install fail2ban
sudo systemctl enable fail2ban
sudo systemctl start fail2ban
sudo systemctl status fail2ban


Fail2ban enhances SSH security by actively responding to suspicious behaviour rather than relying solely on preventative controls.

**fail2ban service running**

<img width="1282" height="342" alt="fail2ban" src="https://github.com/user-attachments/assets/1b21527b-0953-4ae1-a70f-eae52f169e14" />



---

## 6. Security Baseline Verification Script

A script named `security-baseline.sh` was created on the server to verify that key security controls implemented in Weeks 4 and 5 are active.

**Purpose of the script:**
- Verify SSH hardening settings
- Confirm firewall status and rules
- Check AppArmor status
- Confirm fail2ban is running
- Verify automatic updates configuration

**Script location:**  
`/home/adminuser/security-baseline.sh`

The script is designed to be executed remotely via SSH and provides repeatable verification of the server’s security posture.



---

## 8. Weekly Reflection

This week demonstrated how layered security controls work together to strengthen system security. Mandatory access control, automated updates, and fail2ban complement earlier SSH and firewall configurations by providing both preventative and reactive protection.

Creating verification and monitoring scripts reinforced the importance of automation in system administration. These scripts reduce human error, improve repeatability, and provide clear evidence for later auditing and performance analysis. The work completed this week provides a strong foundation for performance testing and security auditing in subsequent phases.


