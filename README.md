# ThreatLens - Threat Intelligence & Attack Surface Mapping Platform

[![Type](https://img.shields.io/badge/Type-Threat%20Intelligence%20Platform-blueviolet?style=flat-square)](https://github.com)
[![Framework](https://img.shields.io/badge/Framework-React%2018%20%2B%20TypeScript-blue?style=flat-square)](https://react.dev)
[![Build](https://img.shields.io/badge/Build-Vite%20v5.4.19-646CFF?style=flat-square)](https://vitejs.dev)
[![Runtime](https://img.shields.io/badge/Runtime-Bun%20v1.3.10-f9f1e1?style=flat-square)](https://bun.sh)
[![Platform](https://img.shields.io/badge/Platform-Kali%20Linux-557C94?style=flat-square)](https://www.kali.org)
[![Status](https://img.shields.io/badge/Status-Deployed-brightgreen?style=flat-square)](https://github.com)

> **Automated threat intelligence & attack surface mapping. Enter a domain to begin reconnaissance.**

ThreatLens is a custom-built, full-stack threat intelligence platform developed and deployed on Kali Linux. It automates domain reconnaissance, surface mapping and security header analysis and generates structured AI-powered findings reports with risk scoring and PDF export.

---

## Table of Contents

- [Overview](#-overview)
- [Tech Stack](#-tech-stack)
- [Prerequisites](#-prerequisites)
- [Installation](#-installation)
- [Launching the Platform](#-launching-the-platform)
- [Using ThreatLens](#-using-threatlens)
- [Scan Results — example.com](#-scan-results--examplecom)
- [Key Findings](#-key-findings)
- [Risk Severity Classification](#-risk-severity-classification)
- [Platform Features](#-platform-features)
- [Skills Demonstrated](#-skills-demonstrated)
- [Disclaimer](#-disclaimer)

---

## Overview

ThreatLens was built to demonstrate dual competency: **security tool development** and **applied threat intelligence analysis**. Unlike off-the-shelf OSINT tools, ThreatLens is architected from source — a production-grade React application with TypeScript, Tailwind CSS and an integrated AI Analyst module that classifies findings and generates remediation-ready reports.

**What it does:**

- Accepts a domain as input and runs an automated multi-vector scan
- Enumerates URLs and maps the visible attack surface
- Detects missing security headers and known vulnerability patterns
- Enriches results with domain registration, hosting and ASN data
- Classifies findings by severity: Critical · High · Medium · Low
- Generates AI Analyst findings with structured remediation guidance
- Exports full PDF reports and exposes raw JSON scan data
- Enforces a Safe-Scanning Policy — users must confirm authorisation before any scan initiates

> All scans in this portfolio were conducted against `example.com`- a known safe, IANA-reserved test target in an authorised, controlled Kali Linux lab environment.

---

## Tech Stack

| Component | Details |
|---|---|
| **Frontend Framework** | React 18 + TypeScript |
| **Build Tool** | Vite v5.4.19 |
| **Package Manager** | Bun v1.3.10 (30e609e0) |
| **Styling** | Tailwind CSS + @tailwindcss/typography v0.5.16 |
| **Bundler Plugin** | @vitejs/plugin-react-swc v3.11.0 |
| **Testing** | @testing-library/react v16.3.1 + jest-dom v6.9.1 |
| **Linting** | ESLint v9.32.0 + @eslint/js v9.32.0 |
| **Node Types** | @types/node v22.16.5 |
| **Operating System** | Kali Linux 2024.x |
| **Interface** | localhost:8080 / 10.0.2.15:8080 |
| **Total Packages** | 538 installed |

---

## Prerequisites

Before installing, ensure the following are available on your Kali Linux machine:

- **Bun** - JavaScript runtime and package manager
  ```bash
  curl -fsSL https://bun.sh/install | bash
  ```
- **Git** — to clone the repository
  ```bash
  sudo apt install git -y
  ```
- **Node.js** (optional fallback) — v18+ recommended

- A modern browser (Firefox on Kali works out of the box)

---

## Installation

### Step 1 - Clone or Download the Repository

If cloning from GitHub:

```bash
git clone https://github.com/YOUR_USERNAME/aegis-intel-scan.git
cd aegis-intel-scan-main
```

Or if downloaded as a ZIP, extract and navigate in:

```bash

cd ~/Downloads/aegis-intel-scan-main
```

### Step 2 - Confirm Project Structure

Verify `package.json` is present before installing:

```bash
ls package.json
# Expected output: package.json
```

### Step 3 - Install Dependencies

Run `bun install` to fetch all 538 packages:

```bash
bun install
```

**Expected output:**

```
[48.53ms] ".env"

bun install v1.3.10 (30e609e0)

+ @eslint/js@9.32.0
+ @tailwindcss/typography@0.5.16
+ @testing-library/jest-dom@6.9.1
+ @testing-library/react@16.3.1
+ @types/node@22.16.5 (v25.5.0 available)
+ @types/react@18.3.23
+ @types/react-dom@18.3.7
+ @vitejs/plugin-react-swc@3.11.0
+ autoprefixer@10.4.21
+ eslint@9.32.0
+ vaul@0.9.9
+ zod@3.25.76
...

538 packages installed [11.64s]

Blocked 2 postinstalls. Run `bun pm untrusted` for details.
```
<img width="1038" height="563" alt="2a" src="https://github.com/user-attachments/assets/d39b66b6-627f-49e1-8089-c75c10021209" />

> If you see a Browserslist warning (`browsers data is 9 months old`), this is non-blocking. Optionally run `npx update-browserslist-db@latest` to resolve it.

---

## Launching the Platform

### Step 4 - Start the Development Server

```bash

bun run dev
```

**Expected output:**

```
VITE v5.4.19  ready in 977 ms

➜  Local:   http://localhost:8080/
➜  Network: http://10.0.2.15:8080/
➜  press h + enter to show help
```
<img width="1038" height="562" alt="2b" src="https://github.com/user-attachments/assets/91301843-1479-4482-892d-3c438882fd39" />

### Step 5 - Open in Browser


Navigate to:

```
http://localhost:8080
```

The ThreatLens interface will load, displaying the domain input field, Safe-Scanning Policy checkbox, and daily scan counter.

---

## Using ThreatLens

### Interface Overview

<img width="1919" height="1089" alt="ThreatLens1" src="https://github.com/user-attachments/assets/2b69642a-e2a5-43ed-9573-3002ed5f0d90" />

The ThreatLens UI provides the following navigation:

| Tab | Description |
|---|---|
| **Dashboard** | Main scan entry point and results overview |
| **History** | Log of previous scan sessions |
| **Compare** | Side-by-side comparison of two scan results |
| **Policies** | Safe-scanning policy settings and AI domain review |
| **Settings** | Platform configuration |

### Running a Scan

1. Navigate to ` http://localhost:8080/`
2. Enter a domain in the input field - e.g. `example.com`
3. Check the **Safe-Scanning Policy** checkbox to confirm you have authorisation to scan the target
4. Click **Scan**
5. Wait for the scan to complete — status will update to `completed.`
6. Review results across the **Findings**, **Attack Surface**, **AI Report**, and **Raw Data** tabs

## Scan Results - example.com

A scan was executed against `example.com` as a safe, authorised test target. ThreatLens returned the following results:

### Summary Dashboard

<img width="1911" height="1070" alt="ThreatLens3" src="https://github.com/user-attachments/assets/9f2f8d62-01f7-4257-92ac-b9db5a8e69de" />

| Metric | Value |
|---|---|
| **Risk Score** | 31 — Medium Risk |
| **URLs Found** | 7 |
| **Vulnerabilities** | 3 |
| **Technologies Detected** | 0 |
| **JS Files** | 0 |
| **Scan Status** | Completed |
| **Scan Duration** | ~2 minutes |

### Domain Enrichment

| Field | Value |
|---|---|
| **Registrar** | RESERVED - Internet Assigned Numbers Authority |
| **Hosting Provider** | Cloudflare, Inc. |
| **ASN** | AS13335 Cloudflare, Inc. |
| **Surface Size** | Small |

---

## Key Findings

<img width="1918" height="1079" alt="ThreatLens5" src="https://github.com/user-attachments/assets/48c0b926-3754-4729-9cb6-c1c31fd30d4d" />
<img width="1893" height="1011" alt="Attack Surface2" src="https://github.com/user-attachments/assets/09727d8f-74ef-4c09-8a61-9a011e4077aa" />


The **AI Analyst** module returned 3 structured findings, all under the **Security Headers** category.
<img width="1521" height="748" alt="AI Analyst Attack Surface" src="https://github.com/user-attachments/assets/4beaad9e-dc14-41ba-8b75-24ef54f97ee9" />
<img width="1922" height="945" alt="Security Header" src="https://github.com/user-attachments/assets/16787729-0430-46f7-ac29-f10364a9d500" />

### HIGH — Missing Content-Security-Policy Header

**Category:** Security Headers

**Description:**
The website does not implement a Content-Security-Policy (CSP) header, leaving it vulnerable to Cross-Site Scripting (XSS) and data injection attacks. Without CSP, browsers cannot distinguish between legitimate and injected scripts, allowing attackers to execute arbitrary JavaScript, steal session cookies, or redirect users to malicious pages.

**Attack Vectors:** XSS · Data Injection

**Remediation:**
```http
Content-Security-Policy: default-src 'self'; script-src 'self' 'nonce-{random}'; object-src 'none';
```
Deploy in `Content-Security-Policy-Report-Only` mode first to identify violations without blocking. Validate at [csp-evaluator.withgoogle.com](https://csp-evaluator.withgoogle.com).

---

### MEDIUM - Missing HSTS Header

**Category:** Security Headers

**Description:**

HTTP Strict Transport Security (HSTS) is not enabled. Without this header, browsers do not enforce HTTPS-only connections, leaving users vulnerable to SSL stripping and protocol downgrade attacks. An attacker with network access can silently intercept encrypted traffic.

**Attack Vectors:** SSL Stripping · Protocol Downgrade

**Remediation:**
```http
Strict-Transport-Security: max-age=31536000; includeSubDomains; preload
```
After confirming HTTPS stability, submit to the HSTS preload list at [hstspreload.org](https://hstspreload.org).

---

### MEDIUM — Missing X-Frame-Options Header

**Category:** Security Headers

**Description:**

The site can be embedded in iframes, enabling clickjacking attacks. An attacker can load the target site invisibly inside a malicious page — tricking users into performing unintended actions such as authorising transactions, changing account settings, or submitting sensitive forms.

**Attack Vectors:** Clickjacking

**Remediation:**
```http
X-Frame-Options: DENY
```
Or use the modern CSP equivalent:
```http
Content-Security-Policy: frame-ancestors 'none';
```
Validate the full header configuration at [securityheaders.com](https://securityheaders.com).

---

## Risk Severity Classification

ThreatLens uses the following severity model:

| Severity | Indicators |
|---|---|
| 🔴 **Critical** | Data leaks, exposed configs, database management tools exposed publicly |
| 🟠 **High** | Missing CSP, accessible admin panels, open redirects |
| 🟡 **Medium** | Missing HSTS / X-Frame-Options, XSS vectors, weak headers |
| 🔵 **Low** | Outdated libraries, excessive dependencies, non-sensitive info leakage |

---

## Platform Features

| Feature | Description |
|---|---|
| **AI Analyst** | AI-generated, structured security findings with severity classification |
| **Findings Tab** | Human-readable vulnerability list with descriptions |
| **Attack Surface Tab** | Enumerated URLs and endpoint mapping |
| **AI Report Tab** | Narrative intelligence report with context and remediation |
| **Raw Data Tab** | Full JSON scan output for downstream tooling or SIEM ingestion |
| **Export PDF** | One-click PDF report generation for client or stakeholder delivery |
| **Scan History** | Persistent log of all previous scans for trend analysis |
| **Compare** | Side-by-side diff of two scan results to track remediation progress |
| **Safe-Scanning Policy** | Mandatory authorisation checkbox — enforces ethical scan practice |
| **Rate Limiting** | 10 scans per day maximum to prevent abuse |
| **AI Domain Policy Review** | Integrated AI policy review before scanning unfamiliar targets |

---

##  Skills Demonstrated

### Security Tool Development
- Built a full-stack threat intelligence application from source on Kali Linux
- React 18 + TypeScript + Vite architecture with Bun package management
- Tailwind CSS responsive UI with security-focused component design
- ESLint and testing-library integration for code quality

### Attack Surface Mapping
- Domain reconnaissance and URL enumeration
- HTTP security header gap analysis
- ASN and hosting provider enrichment
- Risk scoring and surface size classification

### Vulnerability Analysis
- CSP, HSTS and clickjacking attack vector identification
- Risk severity triage and structured finding output
- AI-assisted analysis integration with human-readable reporting

### Reporting & Ethics
- AI-generated PDF reports suitable for client delivery
- Safe-Scanning Policy enforcement built into the platform UI
- Rate-limited scan governance preventing abuse
- Authorised, documented test methodology

---
## Disclaimer

> This project was developed and tested in a **controlled, authorised lab environment** on Kali Linux for cybersecurity portfolio and educational purposes only.
>
> The domain `example.com` was used as the test target — it is an IANA-reserved domain designated specifically for documentation and testing purposes.
>
> **No real organisations, systems, or individuals were targeted without explicit authorisation.**
>
> ThreatLens enforces a built-in Safe-Scanning Policy: users must confirm they hold authorisation to scan any given target before a scan can be initiated.
>
> All activity was conducted ethically and in full compliance with applicable law.

---

## Author

**Oluwaseun Adenuga** — Cybersecurity Analyst & GRC Specialist

[![LinkedIn](https://img.shields.io/badge/LinkedIn-oluwaseunadenuga-0A66C2?style=flat-square&logo=linkedin)](https://www.linkedin.com/in/oluwaseunadenuga)
[![GitHub](https://img.shields.io/badge/GitHub-oluwaseunadenuga-181717?style=flat-square&logo=github)](https://github.com/oluwaseunadenuga)

---

*Portfolio project — ThreatLens Threat Intelligence Platform | Kali Linux · React · Vite · Bun · TypeScript*
