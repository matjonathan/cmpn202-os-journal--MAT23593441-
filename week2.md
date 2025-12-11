# Week 2 – Security Planning & Testing Methodology

## 1. Weekly Overview

**Focus of this week:**  
Plan security controls and performance testing strategy before heavy configuration.

**Date range:** [dd/mm/yyyy – dd/mm/yyyy]

---

## 2. Weekly Objectives

By the end of this week, I aimed to:

1. Design a performance testing methodology for the server.
2. Identify security controls I will implement (firewall, SSH hardening, MAC, etc.).
3. Create an initial threat model for my virtual environment.
4. Decide which metrics and tools I will use for monitoring.

---

## 3. Planned Performance Testing Strategy

### 3.1 Metrics to Collect

I plan to measure:

- CPU usage: [how, e.g. `top`, `htop`, `mpstat`]
- Memory usage: [e.g. `free -h`, `vmstat`]
- Disk I/O: [e.g. `iostat`, `dd`, `fio`]
- Network throughput/latency: [e.g. `ping`, `iperf3`]
- Application-level metrics: [response time using `curl`, `ab`, `wrk`, etc.]

### 3.2 Tools & Rationale

| Tool      | Purpose                    | Why chosen                         |
|-----------|----------------------------|------------------------------------|
| [Tool 1]  | [e.g. CPU & memory]        | [Reason]                           |
| [Tool 2]  | [e.g. Disk I/O]            | [Reason]                           |
| [Tool 3]  | [e.g. Network]             | [Reason]                           |
| [Tool 4]  | [e.g. HTTP benchmarking]   | [Reason]                           |

### 3.3 Baseline vs Load Tests

- **Baseline tests:**
  - Conditions: [e.g. idle system, only SSH session open]
  - Goals: [e.g. measure background resource usage, noise level]

- **Load tests:**
  - How I will generate load: [e.g. run web server, DB queries, stress tools]
  - Duration: [e.g. X minutes per test]
  - Repetitions: [e.g. 3 runs per scenario to average results]

---

## 4. Security Configuration Plan

### 4.1 SSH Hardening Plan

I intend to:

- Use **key-based authentication** instead of passwords.
- Disable root login over SSH.
- (Optional) Change the SSH port from 22 to [port].

Planned config items in `/etc/ssh/sshd_config`:

- `PermitRootLogin no`
- `PasswordAuthentication no`
- [Any other SSH options I plan to use]

### 4.2 Firewall Strategy

Firewall tool: [ufw / iptables / firewalld]

Policy:

- Default incoming: [deny]
- Default outgoing: [allow]
- Allow SSH **only** from workstation IP: `192.168.[X].[workstation]`
- Deny all other inbound traffic by default.

### 4.3 Mandatory Access Control (MAC)

Planned MAC tool: [AppArmor / SELinux]

- Mode: [Enforcing / Permissive]
- Reason for this choice:
  - [e.g. “Supported by my distro”, “Easier profile management”, etc.]

Main idea:

- Confine services so that if one is compromised, its ability to damage the rest of the system is limited.

### 4.4 Automatic Updates & Extra Controls

- Auto security updates using: [e.g. `unattended-upgrades`]
- Intrusion/brute-force protection: [fail2ban or similar]
- Logging plan: [which logs I will use later, e.g. `/var/log/auth.log`, `/var/log/syslog`]

---

## 5. Threat Model

### 5.1 Environment Description

- Server reachable only from workstation via host-only network.
- NAT provides Internet for package updates but not inbound Internet connections.
- Single student administrator (me) with sudo access.

### 5.2 Threats & Mitigations

**Threat 1: [e.g. Brute-force SSH Attack]**

- Scenario: [An attacker guesses passwords over SSH.]
- Impact: [Full server compromise if successful.]
- Likelihood in this environment: [Low/Medium/High]
- Planned mitigations:
  - Key-based authentication.
  - Disable password logins.
  - Firewall restricting SSH to one IP.
  - Fail2ban monitoring SSH login attempts.

**Threat 2: [e.g. Misconfigured Firewall]**

- Scenario: [Accidentally opening unnecessary ports to the host-only network.]
- Impact: [Unnecessary attack surface, increased risk.]
- Mitigations:
  - Default deny policy.
  - Documented rule set.
  - Regular checks (`sudo ufw status` or equivalent).

**Threat 3: [e.g. Privilege Escalation]**

- Scenario: [A user misuses sudo or exploits misconfigured sudo rules.]
- Impact: [Root-level compromise from a user account.]
- Mitigations:
  - Minimal sudo privileges.
  - Careful editing of `/etc/sudoers`.
  - Use of strong passwords and key-based auth.

(Optional: add more threats like weak logging, software vulnerabilities, etc.)

---

## 6. Mapping to Coursework Phases

Explain how this week’s planning supports later phases:

- Links to **Week 4–5**:
  - SSH, firewall, MAC, fail2ban, and automatic updates will be implemented and documented there.
- Links to **Week 6**:
  - Performance testing plan here will guide the tests and metrics I run later.
- Links to **Week 7**:
  - Threat model informs what I check during the security audit (Lynis, nmap, etc.).

---

## 7. Problems Encountered & Solutions

- **Problem:** [e.g. Not sure which metric tools are appropriate]
  - What confused me: [e.g. Too many options, conflicting advice online]
  - How I resolved it: [e.g. Chose simple, standard tools installed by default, tried them briefly]


---

## 8. Reflection (Week 2)

- How threat modelling changed my initial Week 1 design:
- What I learned about planning security and performance **before** configuring:
- How this week’s work will make Weeks 4–7 faster and more structured:
- Any changes I would already make to my original plan after thinking about threats:
