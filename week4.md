# Week 4 – Initial System Configuration & Security Implementation

## 1. Weekly Overview

**Focus of this week:**  
Begin applying concrete security measures to the server, including SSH hardening, firewall configuration, and proper user/privilege management, all accessed via the command line.

**Date range:** [dd/mm/yyyy – dd/mm/yyyy]

---

## 2. Weekly Objectives

By the end of this week, I aimed to:

1. Configure SSH to use key-based authentication instead of passwords.
2. Restrict access to the server using a firewall, limiting SSH to the workstation.
3. Create and use a non-root administrative user for day-to-day administration.
4. Demonstrate that I can fully administer the server remotely via SSH.

---

## 3. SSH Key-Based Authentication

### 3.1 Key Generation on Workstation

On the workstation, I generated an SSH key pair:

```bash
ssh-keygen -t ed25519 -C "[your_key_comment]"
