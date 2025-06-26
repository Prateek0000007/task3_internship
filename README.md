# task3_internship
# 🔐 Vulnerability Scan Report - Cyber Security Internship (OpenVAS Community Edition)

## 📋 Task Description

**Task 3: Perform a Basic Vulnerability Scan on Your PC**  
As part of the cyber security internship, this task involves identifying vulnerabilities in a local system using OpenVAS Community Edition (Greenbone Vulnerability Manager).

---

## 🛠️ Tools Used

- **Operating System:** Parrot OS (Linux)
- **Vulnerability Scanner:** OpenVAS / Greenbone Community Edition
- **Scan Target:** Localhost (`192.168.1.116`)
- **Scan Configuration:** Full and Fast

---

## ✅ Steps Followed

1. Installed OpenVAS (`gvm`) on Parrot OS.
2. Ran `gvm-setup` to sync vulnerability feeds.
3. Started GVM services using `gvm-start`.
4. Accessed the web UI at `https://localhost:9392/`.
5. Created a new target with IP `192.168.1.116`.
6. Created and launched a full vulnerability scan task.
7. Analyzed the results and documented key findings.

---

## 📄 Key Findings

| Vulnerability | Severity | QoD | Port |
|---------------|----------|-----|------|
| SSL/TLS: Certificate Expired | Medium (5.0) | 99% | 443/tcp |
| ICMP Timestamp Detection | Log | 80% | general/icmp |
| Perfect Forward Secrecy Missing | Log | 98% | 443/tcp |
| Report Non-Weak Ciphers | Log | 98% | 443/tcp |
| Greenbone Security Assistant Detected | Log | 80% | 443/tcp |

---

## 🔧 Fixes and Recommendations

- **Renew expired SSL certificate** using Let's Encrypt.
- **Disable ICMP timestamp replies** to reduce OS fingerprinting:
  ```bash
  echo "net.ipv4.icmp_echo_ignore_all=1" | sudo tee -a /etc/sysctl.conf
  sudo sysctl -p
