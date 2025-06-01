# Elevate-Task3
# Task 3 – Local Vulnerability Scan using Nessus Essentials

##  Tool Used
- **Tenable Nessus Essentials**  
- Version: 10.8.4  
- Scan Type: Local authenticated scan  
- OS: Kali Linux  
- Target IP: 192.168.xx.xxx

---

##  Objective
To perform a local vulnerability scan on my Kali Linux system using Nessus and identify security issues related to installed software and configurations.

---

##  Target Details
- **IP Address**: 192.168.XX.XXX  
- **MAC Address**: xx.xx.xx.xx.xx  
- **OS Detected**: Linux Kernel 6.12.25-amd64  
- **Hostname**: kali  

---

##  Summary of Vulnerabilities

| Severity   | Count |
|------------|-------|
| Critical   | 1     |
| High       | 4     |
| Medium     | 2     |
| Low        | 0     |
| Info       | 70    |

---

##  Notable Vulnerabilities Found

### Critical
- **Node.js Multiple Vulnerabilities**  
  Versions below 18.19.1, 20.11.1, or 21.6.2 contain several issues:
  - Path traversal (CVE-2024-21896)
  - Privilege escalation (CVE-2024-21892)
  - Denial of service via HTTP chunked encoding (CVE-2024-22019)  
  **CVSS Score**: 9.8  
  **Fix**: Update Node.js to latest version (20.11.1+ or 21.6.2+)

###  High
- **Python Tornado Library**  
  - Vulnerable to log-based DoS attacks due to improper handling of malformed multipart/form-data  
  - **Fix**: Upgrade Tornado to v6.5.0

- **Node.js Vulnerabilities** from April and July 2024, and May 2025 affecting HTTP/2 handling, HTTP smuggling, and permission models.  
  - **CVEs**: CVE-2024-27982, CVE-2024-27983, CVE-2024-36137, CVE-2025-23167  
  - **Fix**: Upgrade to Node.js 20.19.2 or later

---

##  Other Noteworthy Findings

- **SSL Certificate Cannot Be Trusted**  
  - Self-signed certificate on Nessus web interface  
  - **Fix**: Replace with valid CA-signed certificate (optional for local scanning)

- **Apache Server Detected** (not running)  
  - Version: 2.4.63  
  - Several modules loaded

- **Dockerfiles Detected**  
  - Found in metasploit, dvwa, dnscat2, zphisher, and other tools — potentially sensitive environments

- **Java/OpenJDK Installed**
  - Versions 21.0.7 and 23.0.2

- **Log4j Installed**
  - Version: 2.24.2 — no known vulnerability but worth monitoring

---

##  Screenshots Included

- Nessus dashboard
- Vulnerability overview
- Critical vulnerability (Node.js CVE)
- High vulnerability (Tornado DoS)
- SSL certificate warning

---

##  Recommendations

- Upgrade Node.js and Tornado to patched versions
- Replace or manage self-signed SSL certificates in production
- Monitor Dockerfile exposure
- Keep Apache configuration minimal and secure

---

##  CVSS Overview

- **CVSS v3.1 Critical Score**: 9.8 (Node.js)  
- **VPR Score (Threat Context)**: Ranges from 4.4 to 6.7  
- **EPSS Score**: Up to 0.6955 for certain vulnerabilities

---

##  Key Learnings

- Authenticated Nessus scans reveal deep software-level flaws
- CVSS and VPR scoring help prioritize risks
- Regular patching of common runtimes like Node.js is essential
- Docker environments can increase attack surfaces if mismanaged
