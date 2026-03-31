# Wazuh-EDR-Lab
Wazuh EDR deployment with Sysmon integration on Windows endpoint
# Wazuh EDR Lab with Sysmon Integration

##  Project Overview

This project demonstrates the deployment of an **Endpoint Detection and Response (EDR)** solution using Wazuh, integrated with Sysmon for advanced Windows event monitoring. The lab simulates a basic Security Operations Center (SOC) environment where endpoint activity is continuously monitored, analyzed, and alerted upon.

The implementation focuses on detecting suspicious behavior, monitoring file integrity, and improving endpoint visibility through centralized logging.

---

##  Objectives

* Deploy Wazuh as an EDR and SIEM solution
* Monitor system activity and detect anomalies
* Integrate Sysmon for detailed Windows event logging
* Generate alerts for suspicious or unauthorized actions
* Simulate real-world SOC monitoring workflow

---

##  Lab Architecture

**Environment Setup:**

* **Kali Linux VM** → Wazuh Server (Manager + Dashboard)
* **Windows 10 VM** → Endpoint (Sysmon + Wazuh Agent)
* **Virtualization Platform** → VMware Workstation

**Workflow:**
Windows Endpoint → Sysmon Logs → Wazuh Agent → Wazuh Manager → Dashboard Alerts

---

##  Tools & Technologies

| Tool                  | Purpose                                                   |
| --------------------- | --------------------------------------------------------- |
| Wazuh                 | SIEM & EDR platform for log analysis and threat detection |
| Sysmon (Sysinternals) | Advanced Windows event logging                            |
| Kali Linux            | Hosting Wazuh server                                      |
| Windows 10            | Monitored endpoint                                        |
| VMware Workstation    | Virtual lab environment                                   |
| PowerShell / CMD      | Installation & configuration                              |

---

##  Implementation Steps

### 1️⃣ Environment Setup

* Created two virtual machines using VMware:

  * Kali Linux (Wazuh Server)
  * Windows 10 (Endpoint system)

---

### 2️⃣ Wazuh Installation (Kali Linux)

* Installed Wazuh server components:

  * Wazuh Manager
  * Wazuh Dashboard
* Accessed dashboard via:

  ```
  https://<KALI-IP>
  ```
* Handled browser security warning due to self-signed certificate

---

### 3️⃣ Sysmon Installation (Windows 10)

* Downloaded Sysmon from Sysinternals
* Used a community configuration file for enhanced monitoring

**Installation Command:**

```
sysmon.exe -accepteula -i sysmonconfig-export.xml
```

**Verification Command:**

```
Get-Service Sysmon64
```

---

### 4️⃣ Wazuh Agent Deployment (Windows 10)

* Installed Wazuh agent using MSI package

**Installation Command:**

```
.\wazuh-agent-4.x.x.msi /q WAZUH_MANAGER="192.168.xxx.xxx" WAZUH_AGENT_NAME="Windows_Agent1"
```

**Start Agent:**

```
NET START WazuhSvc
```

---

### 5️⃣ Agent Registration & Monitoring

* Connected Windows endpoint to Wazuh server
* Verified agent status in dashboard
* Monitored:

  * Process creation events
  * File changes
  * System activity logs

---

##  Monitoring & Alerts

* Sysmon logs provided detailed system-level visibility
* Wazuh analyzed logs and generated alerts
* Alerts were triggered for:

  * Suspicious processes
  * Unauthorized activity
  * System changes

This setup simulates a real-world **SOC workflow**, where logs are collected, analyzed, and used for threat detection.

---

##  Data Sources

* Sysmon event logs from Windows endpoint
* Wazuh internal log analysis
* Public threat intelligence (e.g., MalwareBazaar)

---

##  Challenges Faced

* Wazuh service startup delays
* API timeout errors in dashboard
* Agent installation and registration issues
* Network connectivity interruptions
* Troubleshooting service-related errors

---

##  Learning Outcomes

* Practical experience with EDR deployment
* Understanding of SIEM architecture
* Hands-on Sysmon configuration
* Log analysis and alert generation
* Troubleshooting real-world cybersecurity tools

---

##  Project Deliverables

* ✔️ Wazuh EDR deployment
* ✔️ Sysmon integration
* ✔️ Real-time monitoring setup
* ✔️ Alert generation system
* ✔️ Detailed project documentation

---

##  Screenshots

All relevant screenshots of installation, configuration, and alerts are included in this repository.

---

##  Conclusion

This project successfully demonstrates the implementation of a foundational endpoint monitoring system using Wazuh and Sysmon. It highlights the importance of centralized logging, real-time monitoring, and proactive threat detection in modern cybersecurity environments.

The lab reflects a simplified but practical SOC environment used in real-world security operations.

---

##  Author

**Farheen Akhtar**

---

##  Acknowledgment

This project was completed as part of a cybersecurity internship program focused on practical SOC and EDR implementation.
