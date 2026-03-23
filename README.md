# 🚀 Automated Incident Response System

A real-world SOC automation project that integrates SIEM detection with automated incident response using Splunk, Python, and VirusTotal API.

---

## 📌 Project Overview

This project simulates a Security Operations Center (SOC) workflow where security events are detected, enriched, and responded to automatically.

The system detects brute force attacks in Splunk and triggers a Python script to perform threat enrichment, generate reports, and simulate response actions.

---

## 🎯 Key Features

- 🔍 Brute Force Detection using Splunk (Event ID 4625)
- ⚡ Real-time Alert Triggering
- 🤖 Automated Incident Response using Python
- 🌐 Threat Enrichment using VirusTotal API
- 📄 Incident Report Generation (TXT & CSV)
- 🚫 Simulated IP Blocking
- 📊 Structured Logging for Analysis

---

## 🏗️ Architecture


Attacker → Logs → Splunk (SIEM)
↓
Alert Trigger
↓
Python Script
↓
VirusTotal API → Report Generation → Response Action


---

## 🛠️ Technologies Used

- Splunk (SIEM)
- Python
- VirusTotal API
- Sysmon (Log Source)
- CSV / Text Reporting

---

## 🔎 Detection Logic (Splunk SPL)

```spl
index=windows EventCode=4625
| stats count by src_ip, user
| where count > 5
```
💡 Explanation:
Detects multiple failed login attempts
Groups events by source IP
Flags IPs with more than 5 failures as brute force attack

MITRE ATT&CK Mapping: T1110 (Brute Force)

🔔 Alert Workflow
Real-time alert triggers when suspicious activity is detected
Per-result alert ensures each event is processed individually
Executes Python script automatically
Enables automated incident response workflow
🐍 Python Automation Workflow
Key Steps:
Receives IP from Splunk alert (sys.argv)
Queries VirusTotal API for IP reputation
Classifies threat (Malicious / Suspicious / Safe)
Generates incident reports (TXT & CSV)
Simulates response action (IP blocking)
📸 Project Screenshots
🔍 Detection in Splunk

🔔 Alert Configuration

⚙️ Script Execution

📄 TXT Report

📊 CSV Report

📄 Sample Incident Report
INCIDENT RESPONSE REPORT

```
Time: 2026-03-22
IP Address: 8.8.8.8
Threat Level: MALICIOUS
Malicious Score: 1
Suspicious Score: 0
```

Action Taken: Logged & Investigated
💡 Use Case & Impact
Reduces manual effort for SOC analysts
Enables faster threat detection and response
Automates enrichment and reporting
Improves operational efficiency in SOC environments
🚀 Future Enhancements
Email alert integration
Real firewall-based IP blocking
Splunk REST API integration
Dashboard visualization
Full SOAR integration
🏆 Conclusion

This project demonstrates a complete SOC workflow including detection, enrichment, reporting, and response automation.

It reflects real-world security operations and showcases practical skills required for SOC Analyst roles.
