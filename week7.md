## Week 7 – Security Audit and System Evaluation

---

## 1. Weekly Overview

**Focus of this week:**  
Carrying out a final security audit of the server, verifying that all security controls implemented in previous weeks are functioning as intended, evaluating the overall system in terms of security and performance, and reflecting on the full seven-week Operating Systems project.


---

## 2. Weekly Objectives

By the end of this week, I aimed to:

- Perform a system-wide security audit using Lynis.
- Conduct a network security scan using nmap from the workstation.
- Review all running services and justify which services are enabled.
- Verify that SSH hardening, firewall rules, MAC, fail2ban, and automatic updates are functioning correctly.
- Identify any remaining security risks and document potential future mitigations.
- Provide a final evaluation and reflection on the completed system.

---

## 3. Lynis Security Audit

### 3.1 Running the Audit

The Lynis security audit was executed on the server to assess the overall security posture of the operating system and identify potential weaknesses.

**Command executed (on server via SSH):**

sudo lynis audit system



---

### 3.2 Lynis Results Summary

After completing the audit, the following aspects were reviewed:

- Overall Lynis hardening index score
- Warnings related to SSH configuration and authentication
- Firewall and network-related checks
- File permissions and system integrity checks
- Logging and auditing recommendations

Where applicable, previously implemented controls (SSH hardening, firewall rules, AppArmor, fail2ban, and automatic updates) were confirmed as effective through Lynis findings.



---

## 4. Network Security Assessment (nmap)

A network security scan was conducted from the workstation to verify exposed services and confirm firewall restrictions.

**Command executed (on workstation):**

nmap -sS 192.168.56.20



---

## 5. Service Review and Justification

All active services on the server were reviewed to ensure that only essential services were running.

**Command executed (on server via SSH):**

systemctl list-units --type=service --state=running




---

## 6. Verification of Security Controls

The following controls were verified as operational:

- **SSH hardening:** Root login disabled, password authentication disabled, key-based access enforced.
- **Firewall:** UFW enabled with SSH restricted to the workstation IP.
- **Mandatory Access Control:** AppArmor running in enforcing mode.
- **Fail2ban:** Active and monitoring SSH authentication attempts.
- **Automatic updates:** Security updates enabled and configured.

These controls collectively enforce defence-in-depth and were validated through configuration checks, service status outputs, and audit results.

---

## 7. Remaining Risks and Future Mitigations

While the system is securely configured for its intended use, the following potential risks remain:

- Zero-day vulnerabilities in installed software.
- Insider misuse of administrative privileges.
- Limited monitoring depth due to scope constraints.

Potential future mitigations include enhanced logging, centralised monitoring, intrusion detection systems, and more granular access control policies.

---

## 8. Final Evaluation and Reflection

This final audit demonstrated how layered security controls significantly improve the resilience of a Linux server. Implementing SSH hardening, firewall restrictions, mandatory access control, and intrusion prevention created a strong security baseline while maintaining usability.

Across the seven-week project, my understanding of operating system behaviour, security trade-offs, and performance evaluation has significantly improved. The structured, phased approach ensured that planning, implementation, testing, and evaluation were all grounded in professional system administration practices. This project closely mirrors real-world server deployment and management workflows and has strengthened my confidence in administering and securing Linux systems.

