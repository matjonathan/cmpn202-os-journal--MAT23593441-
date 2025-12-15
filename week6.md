## Week 6 – Performance Evaluation and Analysis

---

## 1. Weekly Overview

**Focus of this week:**  
Executing performance tests using the applications selected in Week 3, collecting metrics using command-line tools and monitoring scripts, visualising results, identifying system bottlenecks (CPU, memory, disk, and network), and testing basic performance optimisations.


---

## 2. Weekly Objectives

By the end of this week, I aimed to:

- Execute the planned performance tests under both baseline and load conditions.
- Collect consistent performance data covering CPU, memory, disk I/O, network, and application-level metrics.
- Present results clearly using tables and charts.
- Identify which system resources become bottlenecks in different workload scenarios.
- Apply at least two system or application-level optimisations and compare before-and-after performance metrics.

---

## 3. Testing Methodology

### 3.1 Test Scenarios

Specific test scenarios were defined for each application to represent both baseline and load conditions.

| Application | Scenario Name | Description | Duration |
|------------|---------------|-------------|----------|
| stress-ng | Baseline | System mostly idle with services running but no artificial load | 5 minutes |
| stress-ng | High CPU Load | CPU stress applied across all cores | 5 minutes |
| fio | Disk I/O Test | Sequential and random read/write workload | 5 minutes |
| nginx | HTTP Load Test | HTTP requests generated from workstation | 5 minutes |
| iperf3 | Network Throughput Test | Bandwidth test between workstation and server | 5 minutes |

For each scenario, the following controls were applied:
- Test duration was kept consistent.
- The system started from a similar idle state before each run.
- No additional heavy tasks were run on the host machine during testing.

---

### 3.2 Environment Conditions

**Server:**  
Ubuntu Server (headless), limited RAM and CPU cores allocated via VirtualBox.

**Network:**  
Host-only adapter between workstation and server with no significant external network load.

**Security tools active:**  
UFW firewall, SSH hardening, AppArmor (enforcing), fail2ban, and automatic security updates.

**Monitoring tools used:**
- `monitor-server.sh` script (Week 5)
- Interactive tools: `htop`, `vmstat`, `iostat`, `ss`

---

### 3.3 Measurement Tools

The following tools were used to gather performance data:

- **CPU and memory:** `htop`, `top`, `vmstat`, `ps aux`
- **Disk I/O:** `iostat -xz`, `dd`, `fio`
- **Network:** `ping`, `iperf3`, `ss -tuna`
- **Application-level metrics:** `curl`, `ab` (ApacheBench)
- **Custom logs:** Output from `monitor-server.sh` collected on the workstation

---

## 4. Data Collection

### 4.1 Summary Performance Table

The table below summarises the key metrics observed during each test scenario.  
(Values are populated using the collected results.)

| App | Scenario | CPU Avg (%) | CPU Max (%) | RAM Used (MB) | Disk I/O Summary | Network Summary | Response / Latency Summary | Notes |
|----|---------|-------------|-------------|---------------|------------------|-----------------|----------------------------|------|
| stress-ng | Baseline | | | | Minimal I/O | Minimal traffic | N/A | |
| stress-ng | High CPU Load | | | | Light I/O | Minimal traffic | N/A | CPU saturation observed |
| fio | Disk I/O Test | | | | High throughput / increased await | Minimal traffic | N/A | Disk bottleneck |
| nginx | HTTP Load Test | | | | Log writes observed | Requests/sec measured | Avg and 95th percentile response times | |
| iperf3 | Network Test | | | | Minimal disk usage | High throughput | Latency stable | |

---

### 4.2 Example Raw Outputs

Representative raw outputs are included below to demonstrate how metrics were gathered and interpreted.

#### 4.2.1 vmstat Output

**Command executed:**


vmstat 1 10


This command samples system performance every second for 10 seconds. It provides insight into:
- CPU usage (user, system, idle)
- Memory usage and free memory
- Context switches and interrupts

The output was used to identify CPU saturation and memory pressure during load scenarios.

**vmstat output**


<img width="722" height="380" alt="cpu test" src="https://github.com/user-attachments/assets/84bc7015-ef42-42dc-811b-4d9b37f956a4" />


While stress-ng is running, in another SSH tab or after restarting:

htop


<img width="1277" height="752" alt="image" src="https://github.com/user-attachments/assets/febcb9e7-e029-4ac8-bb8e-9c5ad4fa3e67" />


---

## 5. Initial Bottleneck Analysis

Based on the collected data:
- CPU became the primary bottleneck during stress-ng tests.
- Disk I/O latency increased significantly during fio workloads.
- Network throughput was constrained by the virtualised host-only adapter.
- Memory usage remained stable due to controlled workload sizes.

---

## 6. Optimisation Testing (Preview)

Two optimisations were selected for testing:
- Reducing unnecessary background services.
- Adjusting application-specific settings to reduce resource usage.

Before-and-after measurements are documented and compared in the following section.

---

## 7. Weekly Reflection

This week demonstrated how different workloads stress different system components. Collecting structured performance data made it possible to identify clear bottlenecks rather than relying on assumptions.

The use of scripts and command-line tools ensured repeatable and consistent measurements. This structured testing approach supports meaningful optimisation and prepares the system for the final security audit and evaluation in Week 7.
