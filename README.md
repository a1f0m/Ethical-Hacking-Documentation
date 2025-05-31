# Cybersecurity Lab Documentation

## Overview

This repository contains documentation for various cybersecurity labs covering topics such as:

- SQL Injection
- Path Traversal
- Cross-Site Scripting (XSS)
- File Upload Vulnerabilities
- Access Control Issues
- Cross-Site Request Forgery (CSRF)
- Information Disclosure
- Server-Side Request Forgery (SSRF)

The labs were conducted using tools like **Burp Suite**, **Metasploit**, and **custom scripts** in controlled environments designed for ethical hacking practice.

---

## Table of Contents

- [Day 2: Samba Shell Exploitation](#day-2-samba-shell-exploitation)
- [Day 3: Metasploitable 1 & 2 Exploitation](#day-3-metasploitable-1--2-exploitation)
- [Day 4: Web Application Vulnerabilities](#day-4-web-application-vulnerabilities)
- [Day 5: Advanced Web Exploits](#day-5-advanced-web-exploits)
- [Repository Structure](#repository-structure)
- [Usage](#usage)
- [Disclaimer](#disclaimer)

---

## Day 2: Samba Shell Exploitation

**Objective**  
Gain root access to a target machine by exploiting a vulnerability in Samba version 2.2.1a.

**Steps**

1. **Identify Samba Version**  
   Used `smbclient` to determine the Samba version.

2. **Search for Exploits**  
   Found an exploit for Samba versions < 2.2.8 using `searchsploit`.

3. **Compile and Execute Exploit**  
   Compiled the exploit code and executed it to gain root access.

**Key Commands**
```bash
searchsploit "samba 2.2.1a"
gcc -o exploit 10.c -lcrypto
./exploit -b 0 <target_ip>
```

---

## Day 3: Metasploitable 1 & 2 Exploitation

**Objective**  
Exploit vulnerabilities in Metasploitable 1 and 2 to gain unauthorized access.

**Steps**

1. **Network Scanning**  
   Used `arp-scan` and `nmap` to identify open ports and services.

2. **Exploit Selection**  
   Targeted services like Samba, PostgreSQL, and FTP.

3. **Execution**  
   Used **Metasploit** to gain shell access.

**Key Exploits**

- **Samba**: Remote Code Execution
- **PostgreSQL**: UDF Shared Library Injection
- **FTP (vsFTPd)**: Exploited vsFTPd 2.3.4 backdoor

**Key Commands**
```bash
nmap -sV -p- <target_ip>
msfconsole
use exploit/unix/ftp/vsftpd_234_backdoor
set RHOSTS <target_ip>
run
```

---

## Day 4: Web Application Vulnerabilities

**Labs Covered**

- **SQL Injection**: Bypassed login and extracted data.
- **Path Traversal**: Accessed `/etc/passwd` and other sensitive files.
- **XSS**: Injected scripts into vulnerable input fields.
- **Mitigation Techniques**: Parameterized queries, input validation.

**Key Findings**

- **SQL Injection**: `admin'--` used for login bypass.
- **Path Traversal**: `../../etc/passwd` exposed server files.
- **XSS**: Injected `<script>alert(1)</script>` for JavaScript execution.

---

## Day 5: Advanced Web Exploits

**Labs Covered**

- **File Upload Vulnerabilities**: Uploaded web shells (e.g., PHP).
- **Access Control**: Discovered unprotected admin features.
- **CSRF**: Forged requests to manipulate user settings.
- **Information Disclosure**: Exposed framework versions, config data.
- **SSRF**: Accessed internal endpoints via stock check functions.

**Key Findings**

- **File Upload**: Bypassed content-type filters.
- **Access Control**: Altered cookies/request params for privilege escalation.
- **SSRF**: Accessed localhost services using `127.0.0.1`.

---

## Repository Structure

```
/cybersecurity-labs
│── /Day-2
│   └── Samba_Exploit.md
│── /Day-3
│   └── Metasploitable_Exploits.md
│── /Day-4
│   └── Web_App_Vulnerabilities.md
│── /Day-5
│   └── Advanced_Web_Exploits.md
└── README.md
```

---

## Usage

1. **Clone the repository**
   ```bash
   git clone <repository_url>
   ```

2. **Navigate to any day's folder**  
   For in-depth notes and command references.

3. **Use responsibly**  
   All techniques are for educational and authorized use only.

---

## Disclaimer

These labs were conducted in a **controlled environment** for **educational purposes only**. Unauthorized testing or exploitation of systems is **illegal** and **unethical**. Always obtain **explicit permission** before engaging in any security testing.
