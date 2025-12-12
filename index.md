
# CMPN202 Operating Systems – Technical Journal

**Student Name:** Jonathan Matuka  
**Student ID:** MAT23593441  
**Programme:** BEng Software Engineering  
**Module:** Operating Systems  
**Academic Year:** 2025/26

---

## About This Site

This GitHub Pages site is my **7-week technical journal** for the CMPN202 Operating Systems coursework.

It documents how I:

- Planned and built a **virtualised server + workstation** environment using VirtualBox.
- Administered a **headless Linux server** entirely via the command line and SSH.
- Configured **security controls** (SSH hardening, firewall, MAC, fail2ban, automatic updates).
- Designed and ran **performance tests** for selected applications.
- Performed a final **security audit and system evaluation**.

Each week has its own page with:

- Objectives  
- Commands and configuration steps  
- Screenshots / evidence  
- Analysis (performance / security / trade-offs)  
- Reflection on what I learned  

---

## Weekly Journal Pages

> Click a week to open its page.

- [Week 1 – System Planning & Distribution Selection](week1.md)
- [Week 2 – Security Planning & Testing Methodology](week2.md)
- [Week 3 – Application Selection for Performance Testing](week3.md)
- [Week 4 – Initial System Configuration & Security Implementation](week4.md)
- [Week 5 – Advanced Security & Monitoring Infrastructure](week5.md)
- [Week 6 – Performance Evaluation & Analysis](week6.md)
- [Week 7 – Security Audit & System Evaluation](week7.md)

---

## Quick Navigation

- [Go to Week 1](week1.md) – Environment planning, distro choice, VirtualBox networking, baseline system specs.  
- [Go to Week 2](week2.md) – Security plan, threat model, performance testing strategy.  
- [Go to Week 3](week3.md) – Application selection and installation for performance testing.  
- [Go to Week 4](week4.md) – SSH keys, firewall rules, non-root admin user, remote administration.  
- [Go to Week 5](week5.md) – MAC, automatic updates, fail2ban, security/monitoring scripts.  
- [Go to Week 6](week6.md) – Performance tests, metrics, graphs, bottleneck analysis, optimisations.  
- [Go to Week 7](week7.md) – Lynis audit, nmap scan, service review, final system evaluation.

---

## How This Journal Is Structured

Each weekly page follows a consistent structure:

1. **Weekly Overview** – What that week focused on.  
2. **Objectives** – What I planned to achieve.  
3. **Implementation** – Commands, configuration changes, scripts.  
4. **Evidence** – Screenshots and CLI outputs.  
5. **Analysis** – Performance or security implications, trade-offs.  
6. **Problems & Solutions** – Issues I faced and how I fixed them.  
7. **Reflection** – What I learned and how it links to Operating Systems concepts.

This structure makes it easy to see my progress and how the system evolved over time.

---

## Technologies & Tools Used

- **Virtualisation:** Oracle VirtualBox  
- **Server OS:** [e.g. Ubuntu Server 22.04 LTS]  
- **Workstation:** [e.g. Ubuntu Desktop / Windows host with SSH client]  
- **Remote Access:** OpenSSH (key-based authentication)  
- **Security:** Firewall (e.g. ufw), AppArmor/SELinux, fail2ban, unattended-upgrades  
- **Monitoring & Performance:** `htop`, `vmstat`, `iostat`, `ss`, custom scripts  
- **Audit:** Lynis, nmap  

---

## Notes for Markers

- All work is performed in a **VirtualBox lab environment** as specified in the coursework brief.
- The server is administered **exclusively via SSH**, using a workstation system.
- Screenshots and command outputs are placed on the weekly pages as evidence.
- This homepage provides an overview and links directly to each weekly journal entry.
