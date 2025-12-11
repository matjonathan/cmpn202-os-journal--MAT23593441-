# Week 6 – Performance Evaluation & Analysis

## 1. Weekly Overview

**Focus of this week:**  
Run performance tests using the applications selected in Week 3, collect metrics using CLI tools and scripts, visualise the results, identify bottlenecks (CPU, memory, disk, network), and test basic optimisations.

**Date range:** [dd/mm/yyyy – dd/mm/yyyy]

---

## 2. Weekly Objectives

By the end of this week, I aimed to:

1. Execute the performance tests planned in Week 3 under both baseline and load conditions.
2. Collect consistent performance data (CPU, memory, disk I/O, network, application-level metrics).
3. Create tables and charts to present the results clearly.
4. Identify which resources become bottlenecks in different scenarios.
5. Apply at least two system or application-level optimisations and compare before/after metrics.

---

## 3. Testing Methodology

### 3.1 Test Scenarios

I defined specific test scenarios for each application to represent baseline and load conditions.

Example (adapt with your real tests):

| App | Scenario Name        | Description                                         | Duration |
|-----|----------------------|-----------------------------------------------------|----------|
| [A] | Baseline             | System mostly idle, services running but unused     | [X min]  |
| [A] | High CPU Load        | [Describe CPU stress test or compute-heavy task]   | [X min]  |
| [B] | Disk I/O Test        | [Describe disk read/write or benchmark workload]   | [X min]  |
| [C] | Network / HTTP Load  | [Describe HTTP/Network load from workstation]      | [X min]  |
| [D] | Mixed DB Workload    | [Describe database or mixed workload]              | [X min]  |

For each scenario, I tried to:

- Keep conditions reproducible (same duration, similar starting state).
- Avoid other large background tasks on the host machine.

### 3.2 Environment Conditions

- **Server:** [Distro, RAM, CPU cores, etc. – briefly remind]
- **Network:** Host-only adapter between workstation and server; no significant external load.
- **Security tools running:** [e.g. firewall, fail2ban, MAC, etc., as configured in earlier weeks]
- **Monitoring tools:**  
  - `monitor-server.sh` script from Week 5.  
  - Additional interactive tools: [`htop`, `vmstat`, `iostat`, `ss`, etc.]

### 3.3 Measurement Tools

I used the following tools to gather data:

- **CPU & memory:** `htop`, `top`, `vmstat`, `ps aux`
- **Disk I/O:** `iostat -xz`, `dd`, `fio` (if used)
- **Network:** `ping`, `iperf3` (if available), `ss -tuna`
- **Application-level:** `curl`, `ab`, `wrk`, or application-specific benchmarks
- **Custom logs:** Output from `monitor-server.sh` stored on the workstation

---

## 4. Data Collection

### 4.1 Summary Performance Table

This table summarises key metrics observed in each scenario. Fill in with your real numbers.

| App | Scenario        | CPU Avg (%) | CPU Max (%) | RAM Used (MB) | Disk I/O Summary                   | Network Summary                       | Response / Latency Summary            | Notes |
|-----|-----------------|------------:|------------:|--------------:|------------------------------------|----------------------------------------|----------------------------------------|-------|
| A   | Baseline        |             |             |               | Minimal I/O                        | Minimal traffic                        | N/A                                    |       |
| A   | High CPU Load   |             |             |               | Light I/O                          | Minimal traffic                        | N/A                                    |       |
| B   | Disk I/O Test   |             |             |               | [Throughput / IOPS / high await?]  | Minimal traffic                        | N/A                                    |       |
| C   | HTTP Load Test  |             |             |               | [Reads/writes, log activity]       | [Requests/sec, bandwidth used]         | [Avg/95th percentile response times]   |       |
| D   | DB Workload     |             |             |               | [Random/sequential I/O, latency]   | Possibly low network (if local only)   | [Query latency, ops/sec]               |       |

### 4.2 Example Raw Outputs

Include representative snippets of raw outputs and explain them briefly.

#### 4.2.1 `vmstat`

```bash
vmstat 1 10
