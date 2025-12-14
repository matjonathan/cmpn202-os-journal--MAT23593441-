# Week 1 – System Planning & Distribution Selection

## 1. Weekly Objectives

- Plan my dual-system architecture (server + workstation).
- Choose a Linux server distribution and justify it.
- Decide on workstation option (VM / host / hybrid).
- Plan and document VirtualBox networking and IP addresses.
- Capture baseline system specifications using CLI tools.

## 2. System Architecture Diagram

**Description**

- Server OS: Ubuntu Server 22.04 LTS (headless, no graphical user interface, administered via SSH)
- Workstation OS: Ubuntu Desktop 24.04 LTS (used as the administrative client with SSH installed)
- VirtualBox Networking: Dual-adapter configuration
- Host-Only Adapter (192.168.56.0/24) for secure SSH management between workstation and server
- NAT Adapter (10.0.2.0/24) on the server for outbound Internet access and package updates

**Diagram**

<img width="800" height="800" alt="Concept image" src="https://github.com/user-attachments/assets/ed073e88-7267-47f6-81f8-a83c4354bed7" />


 
The system consists of an Ubuntu Desktop workstation VM and an Ubuntu Server VM running on VirtualBox. The server is headless and administered remotely using SSH.

A Host-Only network (192.168.56.0/24) provides a secure management connection between the workstation (192.168.56.101) and the server (192.168.56.102). The server also uses a NAT interface for outbound Internet access only, allowing system updates without exposing the server to external networks.

This design separates management traffic from Internet access, improving overall system security.



## 3. Distribution Selection Justification

- **Chosen distribution:** Ubuntu Server 22.04 LTS
- **Alternative 1:** Debian 12 (Bookworm)
- **Alternative 2:** Rocky Linux 9 (RHEL-compatible enterprise distribution)

**Why I chose my distro**

- Long-term support:
Ubuntu Server 22.04 LTS provides five years of standard security and maintenance updates, which makes it suitable for long-running server deployments. This aligns well with the coursework requirement to configure, secure, and maintain a system over multiple weeks without frequent disruptive upgrades.
  
- Package ecosystem & documentation:

Ubuntu has a large and well-maintained package repository with up-to-date software available through apt. Most tools required for this project (OpenSSH, fail2ban, monitoring utilities, benchmarking tools, and auditing tools such as Lynis) are available directly from the default repositories. In addition, Ubuntu’s official documentation and community guides are extensive, making it easier to find accurate, beginner-friendly, and advanced configuration references.
  
- Security tools available:

Ubuntu Server includes several security mechanisms that are relevant to operating systems coursework:

- AppArmor enabled by default for mandatory access control (MAC)
- Unattended Upgrades for automatic security patching
- Strong integration with OpenSSH, fail2ban, and firewall tools such as ufw

These features allow security concepts to be implemented and demonstrated clearly without requiring excessive manual configuration
- Community support and learning resources: Ubuntu has one of the largest Linux user communities. This results in abundant tutorials, forums, and troubleshooting resources, which is particularly beneficial in an educational environment. Problems encountered during configuration are more likely to have well-documented solutions, reducing time spent on distribution-specific issues and allowing focus on core operating system concepts.

**Comparison with alternatives**

- Ubuntu vs Debian:

 Debian is known for exceptional stability and conservative package updates. However, this often results in older software versions and slower access to newer features. Debian also requires more manual configuration for certain security and convenience features. Ubuntu, while still stable, provides newer packages, easier initial setup, and better defaults for a teaching environment, making it more suitable for this coursework
- Ubuntu Server vs Rocky Linux:

Rocky Linux is designed as a downstream replacement for Red Hat Enterprise Linux and is primarily targeted at enterprise environments. While it offers strong stability and SELinux by default, it requires more complex configuration and has a steeper learning curve. Ubuntu provides comparable security features with simpler tooling, clearer documentation, and wider community support, making it a better choice for demonstrating operating system concepts in a university setting.

## 4. Workstation Configuration Decision

- **Workstation option chosen:**  
   Option A – Linux Desktop VM 

**Justification**
  
- Consistency and Compatibility
   Using a Linux desktop VM ensures consistency with the Linux server environment. Command-line tools, file system paths, permissions, and networking behaviour are similar across both systems, reducing compatibility issues when administering the server via SSH.
- Isolation and Safety
  Running the workstation as a virtual machine provides isolation from the host operating system. Any configuration errors, misconfigured SSH keys, or networking issues remain contained within the VirtualBox environment and do not affect the host system. 
- Realism and Reproducibility
  This setup closely mirrors real-world administrative workflows, where a Linux workstation is commonly used to manage remote servers. It also allows the environment to be easily reproduced on another machine, which is beneficial for coursework demonstration and assessment.

**Planned tools on workstation**

- SSH Client:
OpenSSH (default on Ubuntu Desktop) for secure remote administration of the server.
- Monitoring and Diagnostic Tools:

htop – real-time process and CPU monitoring

iostat – disk I/O performance analysis

vmstat – memory and system performance statistics

nmon – combined system performance monitoring
- Text Editor / Development Tools:

nano and vim for quick terminal-based editing

Visual Studio Code with Remote SSH extension for editing server configuration files when appropriate


**VirtualBox settings**

- Server Virtual Machine Adapters

Adapter 1: NAT
Purpose: Provides outbound Internet access for the server.
This adapter allows the server to download system updates and install packages while preventing inbound connections from external networks. The NAT network operates on the 10.0.2.0/24 subnet and is used exclusively for Internet connectivity.

Adapter 2: Host-Only Adapter
Purpose: Secure management network between the workstation and the server.
This adapter connects the server to the VirtualBox Host-Only network on the 192.168.56.0/24 subnet. It is isolated from the Internet and is used solely for SSH administration and internal communication.

- Workstation adapters:
  - Adapter 1: NAT
Purpose: Provides Internet access for the workstation.
This allows the workstation to download software, updates, and administrative tools required to manage the server.
  - Adapter 2: Host-Only Adapter
Purpose: Direct, secure connection to the server.
This adapter connects the workstation to the same Host-Only network as the server, enabling SSH access over a private, non-routable network.

**IP addressing**

- Host-Only Network Configuration
  
  -Network: 192.168.56.0/24
  
  -Server IP Address: 192.168.56.102

  -Workstation IP Address: 192.168.56.101

This addressing scheme ensures that both virtual machines can communicate securely while remaining isolated from external networks.ion]`

- How I verified connectivity:  
  -Connectivity between the workstation and the server was verified using the following commands from the workstation:

  -ping 192.168.56.102

- Successful ICMP replies confirmed basic network connectivity.

  
*SSH connectivity was also verified:*

ssh user@192.168.56.102

This confirmed that the Host-Only network was correctly configured and that the server was reachable for remote administration.

This network configuration provides a clear separation between Internet access and management traffic, improving security while maintaining full functionality for system administration.
## 6. System Specifications (CLI Evidence)

Commands (run on **server**):

```bash
uname -a
free -h
df -h
ip addr
lsb_release -a   # or cat /etc/os-release
