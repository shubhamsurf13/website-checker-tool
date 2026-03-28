Here's the complete `README.md` for **RECON-LITE**:

---

```markdown
# 🕵️ RECON-LITE — Website Information Gathering Tool

```
██████╗ ███████╗ ██████╗ ██████╗ ███╗   ██╗
██╔══██╗██╔════╝██╔════╝██╔═══██╗████╗  ██║
██████╔╝█████╗  ██║     ██║   ██║██╔██╗ ██║
██╔══██╗██╔══╝  ██║     ██║   ██║██║╚██╗██║
██║  ██║███████╗╚██████╗╚██████╔╝██║ ╚████║
╚═╝  ╚═╝╚══════╝ ╚═════╝ ╚═════╝ ╚═╝  ╚═══╝
          ██╗     ██╗████████╗███████╗
          ██║     ██║╚══██╔══╝██╔════╝
          ██║     ██║   ██║   █████╗
          ██║     ██║   ██║   ██╔══╝
          ███████╗██║   ██║   ███████╗
          ╚══════╝╚═╝   ╚═╝   ╚══════╝
```

> **A passive OSINT & website reconnaissance tool built for Kali Linux / VMware — no third-party libraries required.**

---

## 📌 Overview

**RECON-LITE** is a terminal-based, cybersecurity-themed passive reconnaissance tool written in pure Python. It gathers publicly available intelligence about any web target including DNS records, WHOIS data, SSL certificates, HTTP headers, open ports, subdomains, geolocation, robots.txt, and technology fingerprints — all from a sleek hacker-style CLI interface.

---

## 🖥️ Requirements

| Requirement | Details |
|-------------|---------|
| Python      | 3.6+    |
| OS          | Linux / Kali Linux / VMware |
| Terminal    | ANSI-color-capable (bash, zsh, xterm) |
| Tools       | `dig` (dnsutils), `whois` — for full DNS & WHOIS support |

### Install system dependencies (Kali / Debian):

```bash
sudo apt update
sudo apt install dnsutils whois -y
```

### No pip installs needed — Standard Library Only!

```
socket, ssl, sys, time, random, os, json, re,
urllib, http, threading, datetime, subprocess
```

---

## 🚀 Installation & Usage

### 1. Clone or Download

```bash
git clone https://github.com/yourname/recon-lite.git
cd recon-lite
```

### 2. Make Executable

```bash
chmod +x reconlite.py
```

### 3. Run

```bash
python3 reconlite.py
```

Or directly:

```bash
./reconlite.py
```

---

## 🎯 Recon Modules

| Option | Module                    | Description |
|--------|---------------------------|-------------|
| `1`    | **Full Scan**             | Runs all modules in sequence |
| `2`    | **IP & DNS Lookup**       | IPv4, reverse DNS, A/MX/NS/TXT records |
| `3`    | **WHOIS Info**            | Registrar, creation/expiry dates, name servers |
| `4`    | **HTTP Headers**          | Server info, security headers, CDN detection |
| `5`    | **SSL Certificate**       | CN, issuer, expiry, SANs, TLS version |
| `6`    | **GeoIP Location**        | Country, city, ISP, ASN, proxy/VPN detection |
| `7`    | **Port Scanner**          | 17 common ports via multithreaded scan |
| `8`    | **Subdomain Scanner**     | Wordlist-based subdomain enumeration |
| `9`    | **Robots.txt Recon**      | Disallowed paths, sitemap discovery |
| `10`   | **Technology Fingerprint**| CMS, frameworks, CDN, JS libraries |
| `0`    | **Exit**                  | Clean session wipe & exit |

---

## 🔍 Module Details

### 🌐 IP & DNS Lookup
- Resolves IPv4 address
- Lists all resolved IPs via `getaddrinfo`
- Performs reverse DNS (PTR) lookup
- Queries A, MX, NS, TXT records via `dig`

### 📋 WHOIS Information
- Registrar name and domain status
- Registrant organization and country
- Created, updated, and expiry dates
- Name servers and DNSSEC status

### 🛡️ HTTP Headers & Security Rating
- Probes both HTTPS and HTTP
- Extracts: `Server`, `X-Powered-By`, `CF-Ray`, `X-Amz-Cf-Id`, `Set-Cookie`, and more
- Security header score out of 5:

| Score | Meaning |
|-------|---------|
| 4–5   | 🟢 Well hardened |
| 2–3   | 🟡 Partial hardening |
| 0–1   | 🔴 Poorly secured |

Security headers checked: `Strict-Transport-Security`, `X-Frame-Options`, `X-XSS-Protection`, `Content-Security-Policy`, `X-Content-Type-Options`

### 🔒 SSL / TLS Certificate
- Common Name, Organization, Issuer
- Valid From / Valid Until dates
- Days until expiry (color-coded)
- Subject Alternative Names (SANs)
- TLS version in use

### 🌍 GeoIP Location
- Country, Region, City
- ISP and Organization
- ASN (Autonomous System Number)
- Timezone and Coordinates
- Proxy / VPN detection flag
- Hosting / Datacenter flag
- Mobile IP detection

*Powered by the free [ip-api.com](http://ip-api.com) endpoint.*

### 🔌 Port Scanner
Multithreaded scan of 17 common ports:

| Port  | Service     | Port  | Service     |
|-------|-------------|-------|-------------|
| 21    | FTP         | 443   | HTTPS       |
| 22    | SSH         | 445   | SMB         |
| 23    | Telnet      | 3306  | MySQL       |
| 25    | SMTP        | 3389  | RDP         |
| 53    | DNS         | 5432  | PostgreSQL  |
| 80    | HTTP        | 6379  | Redis       |
| 110   | POP3        | 8080  | HTTP-Alt    |
| 143   | IMAP        | 8443  | HTTPS-Alt   |
| 27017 | MongoDB     |       |             |

### 🔎 Subdomain Scanner
Probes 40+ common subdomains including:
`www`, `mail`, `admin`, `api`, `dev`, `staging`, `vpn`, `cdn`, `git`, `cpanel`, `webmail`, and more.

### 🤖 Robots.txt Recon
- Fetches `robots.txt` over HTTPS and HTTP
- Extracts all `Disallow` entries (hidden paths)
- Extracts `Sitemap` declarations

### 💻 Technology Fingerprinting
Detects 18+ technologies from headers and page body:

| Category   | Technologies Detected |
|------------|-----------------------|
| CMS        | WordPress, Joomla, Drupal, Shopify, Wix, Squarespace, Magento |
| Frameworks | Laravel, Django, React, Angular, Vue.js |
| Libraries  | jQuery, Bootstrap |
| CDN / Cloud| Cloudflare, AWS |
| Web Server | Nginx, Apache |

---

## 💾 Report Saving

At the end of a Full Scan, you'll be prompted to save a report:

```
Save report to file? (y/n) :
```

If yes, a `.txt` file is generated:

```
recon_example.com_20250428_143022.txt
```

---

## 🛡️ Ethical & Legal Notice

> ⚠️ **This tool is for educational and authorized security research only.**

- Only scan domains you **own** or have **explicit written permission** to test
- Unauthorized scanning may violate the **Computer Fraud and Abuse Act (CFAA)** and similar laws in your jurisdiction
- The author bears no responsibility for misuse of this tool

---

## 📸 UI Preview

```
──────────────────────────────────────────────────────────────
  RECON MODULES :
  [1]  Full Scan          (all modules)
  [2]  IP & DNS Lookup
  [3]  WHOIS Info
  [4]  HTTP Headers
  [5]  SSL Certificate
  [6]  GeoIP Location
  [7]  Port Scanner
  [8]  Subdomain Scanner
  [9]  Robots.txt Recon
  [10] Technology Fingerprint
  [0]  Exit
──────────────────────────────────────────────────────────────

  root@recon:~#
```

---

## 👤 Author

```
Author  : Ghost Protocol
Version : 2.0 Lite
Target  : Kali Linux / VMware
Purpose : Passive recon & OSINT on web targets
```

---

## 📄 License

```
MIT License — Free to use, modify, and distribute with attribution.
For educational and ethical security research purposes only.
```

---

## 🤝 Contributing

```bash
git checkout -b feature/your-module
git commit -m "Add new recon module"
git push origin feature/your-module
```

Pull requests welcome. Open an issue before major changes.

---

> *"Passive recon. Stay in the shadows."*
```

---

Same clean structure as your password analyzer README — covers every module in detail with tables, port listings, tech detection categories, and the ethical disclaimer. Drop it as `README.md` in the same folder. Want both READMEs bundled into one repo `README.md` since they seem to be part of the same **Ghost Protocol** toolkit?
