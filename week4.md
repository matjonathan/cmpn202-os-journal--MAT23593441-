## Week 4 – Initial System Configuration & Security Implementation

---

## 1. Weekly Overview

**Focus of this week:**  
Applying concrete security measures to the server, including SSH key-based authentication, SSH hardening, firewall configuration, and user privilege management. All administration is performed remotely via SSH from the workstation.


---

## 2. Weekly Objectives

By the end of this week, I aimed to:

- Configure SSH to use key-based authentication instead of passwords  
- Restrict server access using a firewall, limiting SSH to the workstation only  
- Create and use a non-root administrative user for daily administration  
- Demonstrate full remote administration of the server via SSH  

---

## 3. SSH Key-Based Authentication

### 3.1 Key Generation on Workstation

An SSH key pair was generated on the workstation to enable secure, passwordless authentication to the server.

**Command executed (on workstation):**

ssh-keygen -t ed25519 -C "cmpn202-ssh-key"


The Ed25519 algorithm was selected due to its strong security and efficiency compared to older key types.

 **<img width="1063" height="488" alt="Workstation SSH" src="https://github.com/user-attachments/assets/2499daf5-3953-4d99-8444-b350e01d0b45" />
 – SSH key generation**



---

### 3.2 Copying the SSH Public Key to the Server

The public SSH key was copied to the server to allow key-based authentication.

**Command executed (on workstation):**

ssh-copy-id adminuser@192.168.56.20


---

### 3.3 Verifying SSH Key Login

A test connection was made to confirm that SSH login works without requiring a password.

**Command executed (on workstation):**



---

## 4. User and Privilege Management

### 4.1 Verifying Non-Root User Access

After logging in via SSH, the active user was verified.

**Command executed (on server via SSH):**

whoami

**Non-root user confirmation**

<img width="330" height="27" alt="whoami" src="https://github.com/user-attachments/assets/0f0f633d-462d-48ab-ac8b-174888a7bd7d" />



---

### 4.2 Verifying Sudo Privileges

Sudo access was tested to confirm controlled privilege escalation.

**Command executed (on server via SSH):**

sudo whoami


The expected output is `root`, confirming correct sudo configuration.

**Sudo privilege verification**

<img width="302" height="47" alt="sudo whoami" src="https://github.com/user-attachments/assets/9258c4ab-2976-407e-a186-13eaf2ed11fb" />



---

## 5. SSH Hardening (Server Configuration)

### 5.1 SSH Configuration Changes

The SSH daemon configuration was edited to enforce secure authentication settings.

**Command executed (on server via SSH):**

sudo nano /etc/ssh/sshd_config


The following settings were applied:

PermitRootLogin no

PasswordAuthentication no

PubkeyAuthentication yes


These changes disable root login, disable password authentication, and enforce key-based access.

**sshd_config hardening**


<img width="202" height="61" alt="sudo nano" src="https://github.com/user-attachments/assets/903263d3-67fe-4236-a4d6-7b6360f7f398" />
