# Week 1 – System Planning & Distribution Selection

## 1. Weekly Objectives

- Plan my dual-system architecture (server + workstation).
- Choose a Linux server distribution and justify it.
- Decide on workstation option (VM / host / hybrid).
- Plan and document VirtualBox networking and IP addresses.
- Capture baseline system specifications using CLI tools.

## 2. System Architecture Diagram

**Description**

- Server OS: [e.g. Ubuntu Server 22.04 LTS, headless]
- Workstation OS: [e.g. Ubuntu Desktop 24.04 / Windows host with SSH client]
- VirtualBox networking: [Host-only / NAT + Host-only / etc.]

**Diagram**

> TODO: Insert a diagram (you can create it in draw.io / PowerPoint / etc., export as PNG, and upload to `images/` in this repo).

Example text description (replace with your own):

- The *server VM* runs on VirtualBox with no GUI, only SSH.
- The *workstation* connects to the server via a Host-Only adapter.
- Optional NAT adapter is used for the server’s Internet access (package updates).

## 3. Distribution Selection Justification

- **Chosen distribution:** [e.g. Ubuntu Server 22.04 LTS]
- **Alternative 1:** [e.g. Debian 12]
- **Alternative 2:** [e.g. CentOS Stream / AlmaLinux / Rocky]

**Why I chose my distro**

- Long-term support: [Your reasoning here]
- Package ecosystem & documentation: [Your reasoning here]
- Security tools available: [e.g. fail2ban, AppArmor, etc.]
- Community support and learning resources: [Your reasoning here]

**Comparison with alternatives**

- Ubuntu vs Debian: [Your comparison – stability, packages, configuration]
- Ubuntu vs [Other distro]: [Your comparison – tools, documentation, etc.]

## 4. Workstation Configuration Decision

- **Workstation option chosen:**  
  [Option A – Linux Desktop VM / Option B – host machine / Option C – hybrid]

**Justification**

- Reasons for this option (performance, convenience, realism):  
  - [Point 1]  
  - [Point 2]  
  - [Point 3]

**Planned tools on workstation**

- SSH client: [e.g. OpenSSH / PuTTY]
- Monitoring tools: [e.g. htop, iostat, vmstat, nmon, etc.]
- Text editor: [nano / vim / VS Code + remote SSH, etc.]

## 5. Network Configuration (VirtualBox & IP Addressing)

**VirtualBox settings**

- Server VM adapters:
  - Adapter 1: [NAT / Host-Only] – [Purpose and details]
  - Adapter 2 (if used): [NAT / Host-Only] – [Purpose and details]

- Workstation adapters:
  - Adapter 1: [NAT / Bridged / Host-Only] – [Details]

**IP addressing**

- Host-Only network:  
  - Network: `192.168.[X].0/24`  
  - Server IP: `192.168.[X].[server]`  
  - Workstation IP: `192.168.[X].[workstation]`

- How I verified connectivity:  
  - `ping 192.168.[X].[server]`  
  - [Any other commands]

## 6. System Specifications (CLI Evidence)

Commands (run on **server**):

```bash
uname -a
free -h
df -h
ip addr
lsb_release -a   # or cat /etc/os-release
