## Incident Response Report

### **Security Alert Monitoring & Incident Response**
* **Prepared by:** Patrick Titus
* **Date:** 29/07/2025

---

### **1. Executive Summary**

This report outlines the detection, analysis, and response to multiple simulated security incidents identified through log analysis using Splunk SIEM. The goal was to mimic real-world SOC operations by reviewing system logs, identifying suspicious activity, classifying alerts by severity, and recommending appropriate mitigation strategies. The simulated incidents included brute-force login attempts, malware alerts, and suspicious IP-based access, all of which were handled following standard incident response practices.

---

### **2. Tools and Environment**

* **SIEM Platform:** Splunk Enterprise (Free Trial)
* **Operating System:** Kali Linux (Virtual Machine)
* **Log Source:** SOC\_Task2\_Sample\_Logs.txt
* **Index Created:** `soc_logs`

---

### **3. Summary of Detected Alerts**

| Alert ID | Description                    | Threat Category     | Severity | Timestamp      |
| -------- | ------------------------------ | ------------------- | -------- | --------------  |
| 001      | Multiple failed login attempts | Brute-force attack  | High     | 2025-07-29 09:02|
| 002      | Malware signature detected     | Malware infection   | High     | 2025-07-29 09:10|
| 003      | Login from unusual IP address  | Unauthorized access | Medium   | 2025-07-29 07:21|
| 004      | Access to admin-only resource  | Privilege misuse    | Medium   | 2025-07-29 02:21|
| 005      | Out-of-hours login             | Policy violation    | Low      | 2025-07-29 10:36|

---

### **4. Timeline of Events**

| Time (UTC)       | Event Description                   | Source IP / Hostname |
| ---------------- | ----------------------------------- | -------------------- |
| 2025-07-29 10:21 | Multiple failed login attempts      | 192.168.1.10 /Charlie|
| 2025-07-29 10:25 | Malware alert triggered             | Bob                  |
| 2025-07-29 10:30 | Login from foreign IP address       | 202.54.1.30/alice    |
| 2025-07-29 10:35 | Attempted access to restricted page | 192.168.1.15/David   |

---

### **5. Threat Analysis**

* **Brute-force Attack:** The system recorded multiple consecutive failed login attempts, consistent with an automated brute-force attempt to compromise credentials.
* **Malware Infection:** The logs included antivirus alerts flagging a known Trojan signature, indicating the presence of potentially harmful software.
* **Unusual IP Activity:** A login attempt from a foreign IP address outside the expected geographic range suggests possible credential theft or unauthorized access.
* **Privilege Abuse:** Access to a restricted administrative endpoint was made by a user account lacking proper privileges—signaling an internal misuse or misconfiguration.

---

### **6. Impact Assessment**

The threats detected, while simulated, represent significant risks in a production environment:

* **Credential Compromise:** Could lead to unauthorized access to sensitive systems.
* **Malware Activity:** May result in data exfiltration, system downtime, or lateral movement within the network.
* **Policy Violations:** Indicate gaps in access control or user training, which could escalate if exploited.

---

### **7. Remediation Recommendations**

| Threat Category    | Recommended Response                                      |
| ------------------ | --------------------------------------------------------- |
| Brute-force attack | Enforce account lockout policy and enable MFA             |
| Malware infection  | Isolate affected host, run full malware scan, and reimage |
| Unusual login      | Implement IP-based geofencing and alerting                |
| Privilege misuse   | Audit user roles, apply least privilege principle         |

---
