# Week 3 – Application Selection for Performance Testing

## 1. Weekly Overview

**Focus of this week:**  
Select and install applications that will generate meaningful workloads (CPU, memory, disk, network) for performance testing.

**Date range:** [dd/mm/yyyy – dd/mm/yyyy]

---

## 2. Weekly Objectives

1. Choose a set of applications representing different workload types.
2. Install and configure these applications via SSH.
3. Predict their resource usage profile.
4. Plan how they will be used in later performance tests.

---

## 3. Application Selection Matrix

Use this table to justify each choice.

| Application | Category (CPU/RAM/I/O/Network/Server) | Why I chose it | Expected use case |
|------------|----------------------------------------|----------------|-------------------|
| [App 1]    | [e.g. CPU-intensive]                   | [Reason]       | [Scenario]        |
| [App 2]    | [e.g. Disk I/O]                        | [Reason]       | [Scenario]        |
| [App 3]    | [e.g. Network server]                  | [Reason]       | [Scenario]        |
| [App 4]    | [e.g. Database / mixed]                | [Reason]       | [Scenario]        |

---

## 4. Installation & Configuration Steps

For each application, record installation and any config changes.

### 4.1 [Application 1 – Name]

**Commands executed:**

```bash
sudo apt update
sudo apt install [package-name]
# Any extra commands
