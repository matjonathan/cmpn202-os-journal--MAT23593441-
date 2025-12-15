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

The following applications were selected to represent different workload types commonly encountered on Linux servers. This allows operating system behaviour to be evaluated under varied and realistic conditions.

| Application | Category | Why I Chose It | Expected Use Case |
|------------|----------|---------------|------------------|
| stress-ng | CPU / RAM intensive | Designed specifically to stress CPU cores and memory, making it ideal for controlled load testing | Simulating high CPU and memory pressure to analyse scheduling and resource allocation |
| fio | Disk I/O intensive | Industry-standard benchmarking tool for testing disk read/write performance | Evaluating disk throughput, latency, and I/O wait under synthetic workloads |
| iperf3 | Network intensive | Widely used tool for measuring network throughput and performance | Testing bandwidth and network performance between workstation and server |
| nginx | Server / mixed workload | Lightweight and commonly used web server | Simulating a real server application handling client requests |

---

## 4. Installation and Configuration Steps

All applications were installed on the server via SSH using the command line. No graphical tools were used.

### 4.1 stress-ng (CPU and Memory Testing)

**Commands executed:**

- sudo apt update
- sudo apt install stress-ng



**Configuration notes:**  
No additional configuration is required. Workload parameters (CPU cores, memory usage, duration) will be specified at runtime during testing.

---

### 4.2 fio (Disk I/O Testing)

**Commands executed:**

- sudo apt update
- sudo apt install fio

  
**Configuration notes:**  
Disk I/O behaviour will be defined using command-line options during testing to simulate sequential and random read/write workloads.

---

### 4.3 iperf3 (Network Performance Testing)

**Commands executed:**

- sudo apt update
- sudo apt install iperf3

  
**Configuration notes:**  
The server will run `iperf3` in server mode during network tests, while the workstation will act as the client.

---

### 4.4 nginx (Server Application)

**Commands executed:**

- sudo apt update
- sudo apt install nginx

  
**Configuration notes:**  
The default nginx configuration will be used initially to provide a baseline. Any later configuration changes will be documented and justified during performance optimisation testing.

---

These applications provide a balanced mix of synthetic and real-world workloads, enabling comprehensive performance evaluation in later phases of the coursework.
