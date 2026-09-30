# network-security-investigation-lab
Network Security Investigation Lab

## Project Overview

This project demonstrates the investigation of suspicious network activity using packet analysis, network enumeration, and incident documentation techniques commonly used by NOC Analysts, Network Analysts, SOC Analysts, and Cybersecurity Analysts.

The objective is to identify potential threats, analyze network traffic, document findings, and provide remediation recommendations.

---

## Scenario

A workstation on the internal network is suspected of communicating with unauthorized external systems.

As the analyst, the goal is to:

1. Identify active hosts
2. Discover open ports
3. Analyze network traffic
4. Detect suspicious activity
5. Assess risk
6. Recommend remediation

---

# Network Topology

```

Internet
|
Firewall
|
Switch
|
|------- Analyst Workstation
|------- User Workstation
|------- Web Server

```

---

# Phase 1: Network Discovery

## Objective

Identify active hosts within the environment.

### Example Commands

```bash
ping 192.168.1.10

ping 192.168.1.20

ping 192.168.1.30
```

### Findings

| IP Address | Status |
|------------|---------|
| 192.168.1.10 | Online |
| 192.168.1.20 | Online |
| 192.168.1.30 | Online |

---

# Phase 2: Port Scanning

## Objective

Identify exposed services.

### Nmap Scan

```bash
nmap -sV 192.168.1.20
```

### Results

| Port | Service |
|--------|---------|
| 22 | SSH |
| 80 | HTTP |
| 443 | HTTPS |

### Risk Assessment

Open services should be reviewed regularly to ensure they are necessary and properly secured.

---

# Phase 3: Traffic Analysis

## Objective

Analyze captured network traffic.

### Wireshark Filters

DNS Traffic

```text
dns
```

HTTP Traffic

```text
http
```

TCP Connections

```text
tcp
```

Failed Connections

```text
tcp.flags.reset == 1
```

---

# Investigation Findings

## Observation 1

Multiple DNS requests were observed from a workstation.

### Assessment

This behavior appears normal.

---

## Observation 2

Repeated outbound connections to an unfamiliar IP address were identified.

### Assessment

Requires further investigation.

---

## Observation 3

Several failed connection attempts were detected.

### Assessment

May indicate scanning activity or service misconfiguration.

---

# Incident Report

## Incident ID

IR-001

## Severity

Medium

## Description

A workstation generated repeated outbound connections to an unfamiliar external destination.

## Impact

Potential data exposure risk.

## Evidence

- DNS queries observed
- Multiple outbound connections
- Failed connection attempts

## Root Cause

Unknown

## Recommended Actions

1. Review endpoint logs
2. Validate destination reputation
3. Verify user activity
4. Monitor future connections
5. Implement additional alerting

---

# Lessons Learned

- Continuous monitoring improves visibility.
- Packet analysis helps identify unusual behavior.
- Proper documentation supports incident response.
- Network baselines are critical for anomaly detection.

---

# Skills Demonstrated

- Network Monitoring
- Packet Analysis
- TCP/IP
- DNS Analysis
- Incident Documentation
- Risk Assessment
- Troubleshooting
- Security Investigation

---

# Tools Used

- Wireshark
- Nmap
- Linux
- GitHub

---

# Analyst Notes

This project was created for cybersecurity and networking portfolio development and demonstrates investigation methodology rather than production network analysis.
