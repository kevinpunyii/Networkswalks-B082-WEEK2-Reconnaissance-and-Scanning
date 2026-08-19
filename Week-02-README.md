# 🛡️ Week 02 — Reconnaissance & Footprinting Lab

### NetworkWalks Cybersecurity Internship | GitHub Project

![Week](https://img.shields.io/badge/Week-02-blue)
![Focus](https://img.shields.io/badge/Focus-Reconnaissance%20%26%20OSINT-orange)
![Platform](https://img.shields.io/badge/Platform-Kali%20Linux%20%7C%20Maltego%20%7C%20Zenmap-black)
![Status](https://img.shields.io/badge/Status-In%20Progress-yellow)
![Use](https://img.shields.io/badge/Use-Educational%20Only-green)

> **Purpose:** This repository records my Week 02 practical work, including reconnaissance, OSINT, search-engine footprinting, graph-based analysis, host discovery and network mapping.
>
> **Important:** All screenshots in this repository must be my own screenshots captured while performing the assigned exercises. Example/reference screenshots must not be submitted as personal evidence.

---

## 📑 Contents

- [1. Project Overview](#1-project-overview)
- [2. Scope and Responsible Use](#2-scope-and-responsible-use)
- [3. Learning Objectives](#3-learning-objectives)
- [4. Tools Used](#4-tools-used)
- [5. Practical Modules](#5-practical-modules)
  - [W2-PM1 — Kali Footprinting Toolkit](#w2-pm1--kali-footprinting-toolkit)
  - [W2-PM2 — GHDB Footprinting](#w2-pm2--ghdb-footprinting)
  - [W2-PM3 — Maltego Footprinting](#w2-pm3--maltego-footprinting)
  - [W2-PM4 — theHarvester Footprinting](#w2-pm4--theharvester-footprinting)
  - [W2-PM5 — Zenmap Network Scanning](#w2-pm5--zenmap-network-scanning)
- [6. Evidence Checklist](#6-evidence-checklist)
- [7. Security Observations](#7-security-observations)
- [8. Recommendations](#8-recommendations)
- [9. Conclusion](#9-conclusion)
- [10. Repository Structure](#10-repository-structure)
- [11. Final Submission Checklist](#11-final-submission-checklist)

---

# 1. Project Overview

Week 02 focuses on the reconnaissance stage of a cybersecurity assessment. The practical work moves from collecting publicly available domain information to identifying indexed resources, visualising relationships between digital entities, gathering public host information and finally discovering devices on an authorised local network.

The project is divided into five practical modules:

| Module | Practical | Main Focus |
|---|---|---|
| **W2-PM1** | Kali Footprinting Toolkit | WHOIS, web fingerprinting, DNS and WAF information |
| **W2-PM2** | GHDB Footprinting | Search-engine reconnaissance and indexed exposure |
| **W2-PM3** | Maltego | Visual OSINT and relationship mapping |
| **W2-PM4** | theHarvester | Public host and information harvesting |
| **W2-PM5** | Zenmap | Local host discovery and topology |

The assignment requires at least one elective module together with the essential Zenmap module and the final report. This repository documents all five modules where completed.

---

# 2. Scope and Responsible Use

This project is intended for **educational cybersecurity training**.

The activities are limited to:

- The target/domain assigned by the internship.
- Publicly available information where the exercise is passive OSINT.
- My own or explicitly authorised local network for Zenmap/Nmap discovery.
- Systems and information for which testing or collection is permitted.

### Out of scope

The following are not part of this project:

- Unauthorised access.
- Credential theft or password attacks.
- Exploitation of discovered vulnerabilities.
- Denial-of-service activity.
- Modification or deletion of data.
- Accessing private accounts or restricted information.

> **Security note:** A discovered hostname, IP address, email address, technology, or open service is an observation. It should not automatically be described as a confirmed vulnerability.

---

# 3. Learning Objectives

Through these exercises, I aimed to:

1. Understand the purpose of reconnaissance in cybersecurity.
2. Practise passive and authorised information gathering.
3. Identify information exposed through DNS and web technologies.
4. Understand how search engines can index unintentionally exposed resources.
5. Use Maltego to represent relationships between digital entities.
6. Use theHarvester to collect publicly available hosts and related information.
7. Use Zenmap/Nmap to discover active hosts on an authorised network.
8. Record commands, observations and screenshots in a professional format.
9. Distinguish between an information disclosure and a confirmed security vulnerability.
10. Understand why reducing unnecessary public exposure is important for security.

---

# 4. Tools Used

| Tool | Role in the Project |
|---|---|
| **Kali Linux** | Security-testing environment used for the command-line reconnaissance exercises |
| **WHOIS** | Domain registration and nameserver information |
| **WhatWeb** | Web-server and technology fingerprinting |
| **nslookup** | DNS name resolution |
| **curl** | HTTP response/header inspection |
| **Wafw00f** | Web Application Firewall identification |
| **DNSRecon** | DNS record enumeration |
| **Google / GHDB** | Search-engine reconnaissance |
| **Maltego** | Graph-based OSINT and entity relationship analysis |
| **theHarvester** | Public host/email/subdomain collection |
| **Zenmap / Nmap** | Host discovery and network topology visualisation |

---

# 5. Practical Modules

## W2-PM1 — Kali Footprinting Toolkit

### Objective

The purpose of PM1 is to understand how several small reconnaissance utilities can be combined to create a technical profile of a domain.

### Tools used

- WHOIS
- WhatWeb
- nslookup
- curl
- Wafw00f
- DNSRecon

### 5.1 WHOIS

**Command used:**

```bash
whois networkwalks.com
```

### What I checked

The WHOIS output was reviewed for publicly available registration information, registrar details, registration dates and authoritative nameservers.

### Evidence

**Screenshot: `screenshots/pm1-whois.png`**

![PM1 - WHOIS](./screenshots/pm1-whois.png)

---

### 5.2 WhatWeb

**Command used:**

```bash
whatweb networkwalks.com
```

### What I checked

WhatWeb was used to identify technologies exposed by the website, including the web server and application/platform indicators.

The captured result identified the website at:

`192.232.216.135`

and reported Apache/WordPress-related technology information.

### Evidence

**Screenshot: `screenshots/pm1-whatweb.png`**

![PM1 - WhatWeb](./screenshots/pm1-whatweb.png)

---

### 5.3 nslookup

**Command used:**

```bash
nslookup networkwalks.com
```

### Observation

The DNS lookup returned:

`192.232.216.135`

This provided an independent DNS resolution result for the domain.

### Evidence

**Screenshot: `screenshots/pm1-nslookup.png`**

![PM1 - nslookup](./screenshots/pm1-nslookup.png)

---

### 5.4 curl

**Command used:**

```bash
curl -I https://networkwalks.com
```

### What I checked

The HTTP response headers were inspected for information such as the HTTP status, server information, security-related headers and application-related response details.

The captured output returned an HTTP `200` response and exposed technical header information including Apache and WordPress-related links.

### Evidence

**Screenshot: `screenshots/pm1-curl.png`**

![PM1 - curl](./screenshots/pm1-curl.png)

---

### 5.5 Wafw00f

**Command used:**

```bash
wafw00f networkwalks.com
```

### Observation

The captured result identified **ModSecurity (SpiderLabs)** as the web application firewall protecting the site.

### Evidence

**Screenshot: `screenshots/pm1-wafw00f.png`**

![PM1 - Wafw00f](./screenshots/pm1-wafw00f.png)

---

### 5.6 DNSRecon

**Command used:**

```bash
dnsrecon -d networkwalks.com
```

### What I checked

DNSRecon was used to enumerate publicly available DNS information, including:

- SOA
- NS
- MX
- TXT/SPF
- SRV records

The captured output also showed cPanel autodiscover-related records.

### Evidence

**Screenshot: `screenshots/pm1-dnsrecon.png`**

![PM1 - DNSRecon](./screenshots/pm1-dnsrecon.png)

---

### PM1 Summary

PM1 demonstrated that different reconnaissance tools reveal different parts of the same public-facing infrastructure. Registration information, DNS records, web technologies, HTTP headers and WAF information can be combined to create a broader reconnaissance picture.

---

# W2-PM2 — GHDB Footprinting

## Objective

The purpose of PM2 is to understand how search engines can expose information that has already been indexed publicly.

### Method

The exercise uses advanced search operators associated with Google Hacking Database (GHDB) techniques. The activity is focused on **search-engine indexing**, rather than directly attacking the discovered resources.

### Search evidence

**Screenshot: `screenshots/pm2-ghdb-search.png`**

![PM2 - GHDB Search](./screenshots/pm2-ghdb-search.png)

### Result evidence

**Screenshot: `screenshots/pm2-ghdb-result.png`**

![PM2 - GHDB Result](./screenshots/pm2-ghdb-result.png)

> **Replace the two PM2 image filenames above if your actual screenshot names are different.**

### Observation

The exercise demonstrates that information does not have to be actively attacked to become discoverable. If a device, directory, document or other resource is indexed by a search engine, an attacker may be able to locate it using carefully constructed search queries.

### Security lesson

Organisations should periodically review what their public-facing systems allow search engines to index and should remove or restrict content that was never intended to be publicly discoverable.

---

# W2-PM3 — Maltego Footprinting

## Objective

The purpose of PM3 is to use Maltego as a visual OSINT platform and understand how separate pieces of public information can be represented as connected entities.

### Procedure

1. Opened Maltego Desktop.
2. Created a Domain entity.
3. Entered the assigned domain information.
4. Selected the available footprinting/OSINT transforms.
5. Examined the resulting entities and relationships.
6. Captured the graph and entity details as evidence.

### Evidence — Screenshot 1

**Screenshot: `screenshots/maltego1.png`**

![PM3 - Maltego Setup](./screenshots/maltego1.png)

This screenshot shows the initial Maltego domain entity and the target configuration.

### Evidence — Screenshot 2

**Screenshot: `screenshots/maltego2.png`**

![PM3 - Maltego Graph Results](./screenshots/maltego2.png)

> **Reserved for the second Maltego PNG.**
>
> Use the second screenshot to show the populated graph/transform results after the analysis has been performed.

### Observation

Maltego makes relationships easier to understand visually. Instead of examining individual pieces of information separately, related domains, email addresses, DNS information and infrastructure entities can be represented as nodes and links.

### Security lesson

A single public data point may appear harmless, but several related pieces of information can reveal a much clearer picture of an organisation's digital footprint.

---

# W2-PM4 — theHarvester Footprinting

## Objective

The purpose of PM4 is to understand how OSINT aggregation tools can collect publicly available hosts and related information from configured sources.

### Tool

**theHarvester**

### Initial tool check

The following command was used to view the available options:

```bash
theHarvester -h
```

### Evidence — Tool Help

**Screenshot: `screenshots/theharvester-help.png`**

![PM4 - theHarvester Help](./screenshots/theharvester-help.png)

> This screenshot is supporting evidence only. The main PM4 evidence is the actual harvesting result.

---

### Footprinting command

The captured practical run used:

```bash
theHarvester -d microsoft.com -l 1000 -b duckduckgo
```

### Observed result

The captured output showed:

- Target: `microsoft.com`
- Search source: DuckDuckGo
- IP addresses found: `0`
- Emails found: `0`
- People found: `0`
- Hosts found: `27`

The output displayed a list of Microsoft-related hostnames.

### Main Evidence

**Screenshot: `screenshots/theharvester-results.png`**

![PM4 - theHarvester Results](./screenshots/theharvester-results.png)

### Observation

The exercise demonstrates how an OSINT aggregation tool can collect host information from publicly available search-engine data without requiring direct exploitation of the target.

### Security lesson

Publicly discoverable hostnames can provide useful information about an organisation's external attack surface. Organisations should monitor their public DNS and hostname footprint and remove unnecessary exposure where possible.

---

# W2-PM5 — Zenmap Network Scanning

## Objective

PM5 is the essential network-discovery module. The purpose is to identify active hosts on an authorised local network and understand how those hosts can be represented visually.

> **Important:** Zenmap/Nmap scanning should only be performed against a network that I own or have explicit permission to test.

### Scan performed

The supplied Zenmap evidence shows a Ping Scan using:

```bash
nmap -sn 10.0.2.2
```

### Observation

The scan identified the target host as active and displayed its MAC address information. The Zenmap host list also contained:

- `10.0.0.1`
- `10.0.2.2`
- `192-232-216-135`

### Evidence — Zenmap Scan

**Screenshot: `screenshots/zenmap1.png`**

![PM5 - Zenmap Scan](./screenshots/zenmap1.png)

---

### Evidence — Zenmap Topology

The topology view visually represents the discovered hosts and their relationship to the local host.

**Screenshot: `screenshots/zenmap2.png`**

![PM5 - Zenmap Topology](./screenshots/zenmap2.png)

### Observation

The topology view provides a faster visual understanding of the hosts discovered during network reconnaissance.

### Security lesson

Network discovery is useful for defensive inventory as well as security assessment. An organisation should know which devices are connected to its network, whether those devices are expected, and what services they expose.

---

# 6. Evidence Checklist

Before pushing the repository to GitHub, make sure the `screenshots` directory contains the evidence files.

### PM1 — Kali Footprinting

- [ ] `pm1-whois.png`
- [ ] `pm1-whatweb.png`
- [ ] `pm1-nslookup.png`
- [ ] `pm1-curl.png`
- [ ] `pm1-wafw00f.png`
- [ ] `pm1-dnsrecon.png`

### PM2 — GHDB

- [ ] `pm2-ghdb-search.png`
- [ ] `pm2-ghdb-result.png`
- [ ] Any additional screenshots specifically required by the assignment

### PM3 — Maltego

- [ ] `maltego1.png`
- [ ] `maltego2.png` ← **reserved for your second Maltego PNG**

### PM4 — theHarvester

- [ ] `theharvester-help.png` — optional/supporting
- [ ] `theharvester-results.png` — **main evidence**

### PM5 — Zenmap

- [ ] `zenmap1.png`
- [ ] `zenmap2.png`

---

# 7. Security Observations

The practical exercises produced several useful reconnaissance lessons.

| Observation | Security significance |
|---|---|
| Domain registration information is publicly available | Helps build an initial profile of a domain |
| DNS records reveal infrastructure relationships | Can expose mail, hosting and service information |
| Web technology can sometimes be fingerprinted | Helps an attacker identify technologies that require patching |
| HTTP headers may disclose implementation details | Unnecessary information can increase reconnaissance value |
| WAF technology may be identifiable | Reveals part of the site's defensive architecture |
| Search engines can index unintended resources | Public indexing can increase exposure |
| OSINT can connect otherwise separate data points | Relationships may reveal more than individual records |
| Public hostnames can be collected automatically | Increases visibility of an organisation's external footprint |
| Local network discovery reveals active devices | Useful for asset inventory and defensive monitoring |

> These observations describe reconnaissance exposure. They should not be interpreted as confirmed exploitable vulnerabilities unless a separate authorised security test proves exploitation is possible.

---

# 8. Recommendations

Based on the lessons from the practical modules, the following defensive measures are recommended:

1. **Reduce unnecessary information disclosure** — avoid exposing software versions and infrastructure details when they are not required.
2. **Keep web applications updated** — patch CMS platforms, plugins and supporting software regularly.
3. **Review HTTP headers** — remove unnecessary response information where possible.
4. **Audit DNS records** — remove obsolete or unnecessary records.
5. **Monitor search-engine exposure** — periodically review what public search engines can discover.
6. **Protect publicly accessible devices** — especially cameras, routers, management interfaces and IoT systems.
7. **Review the organisation's OSINT footprint** — identify information that can be combined by an external observer.
8. **Maintain an accurate network inventory** — investigate unexpected devices promptly.
9. **Secure administrative interfaces** — restrict management services and use strong authentication.
10. **Stay within authorised scope** — never apply reconnaissance or scanning techniques to systems without permission.

---

# 9. Conclusion

Week 02 provided practical experience with several reconnaissance approaches.

The Kali exercises showed how individual utilities can reveal registration, DNS, web and WAF information. GHDB techniques demonstrated the importance of search-engine indexing. Maltego showed how public information can be connected visually. theHarvester demonstrated automated collection of publicly available host information. Zenmap then provided a practical view of active hosts and network topology on an authorised environment.

The main lesson is that cybersecurity does not begin with exploitation. A considerable amount of information can be learned before any attempt is made to access a system. Understanding this reconnaissance process helps defenders identify unnecessary exposure, maintain better asset inventories and improve the overall security posture of an organisation.

---

# 10. Repository Structure

Recommended GitHub structure:

```text
Week-02-Cybersecurity/
│
├── README.md
│
├── screenshots/
│   ├── pm1-whois.png
│   ├── pm1-whatweb.png
│   ├── pm1-nslookup.png
│   ├── pm1-curl.png
│   ├── pm1-wafw00f.png
│   ├── pm1-dnsrecon.png
│   │
│   ├── pm2-ghdb-search.png
│   ├── pm2-ghdb-result.png
│   │
│   ├── maltego1.png
│   ├── maltego2.png
│   │
│   ├── theharvester-help.png
│   ├── theharvester-results.png
│   │
│   ├── zenmap1.png
│   └── zenmap2.png
│
└── report/
    └── Week-02-Final-Report.pdf
```

---

# 11. Final Submission Checklist

Before submitting the GitHub repository:

- [ ] README opens correctly on GitHub.
- [ ] All screenshot filenames match the Markdown image paths.
- [ ] Every screenshot is my own captured evidence.
- [ ] PM1 contains all six required tool screenshots.
- [ ] PM2 contains the actual GHDB screenshots.
- [ ] PM3 contains **both Maltego screenshots**.
- [ ] PM4 contains the actual theHarvester result screenshot.
- [ ] PM5 contains the Zenmap scan and topology screenshots.
- [ ] No sample screenshot is presented as personal work.
- [ ] No unsupported findings have been added.
- [ ] Target/scope information is accurate.
- [ ] The final report contains the same evidence as the GitHub repository.
- [ ] Personal information that does not need to be public has been removed.
- [ ] The repository does not contain passwords, API keys, tokens or other secrets.

---

## 📌 Final Note

This README is written as an original project document rather than reproducing the wording of the reference material. The evidence sections are deliberately tied to the practical screenshots and outputs.

**Week 02 — Reconnaissance, OSINT & Network Discovery**

*Cybersecurity Internship Practical Project*
