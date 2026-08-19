# 🛡️ Week 02 --- Reconnaissance, OSINT & Network Discovery

### NetworkWalks Cybersecurity Internship --- Practical Project

![Week](https://img.shields.io/badge/Week-02-blue)
![Focus](https://img.shields.io/badge/Focus-Reconnaissance%20%26%20OSINT-orange)
![Platform](https://img.shields.io/badge/Platform-Kali%20Linux%20%7C%20Maltego%20%7C%20Zenmap-black)
![Status](https://img.shields.io/badge/Status-Completed%20Selected%20Modules-success)
![Use](https://img.shields.io/badge/Use-Educational%20Only-green)

> **Project purpose**
>
> This repository documents my Week 02 practical cybersecurity work,
> with an emphasis on reconnaissance, OSINT, web/DNS footprinting,
> visual relationship mapping, public host discovery, and authorised
> network discovery.

> **Evidence rule**
>
> All screenshots used as evidence must be my own screenshots captured
> while performing the assigned exercises. Reference or example
> screenshots must not be presented as personal evidence.

------------------------------------------------------------------------

## 📑 Contents

1.  [Project Snapshot](#1-project-snapshot)
2.  [Scope & Responsible Use](#2-scope--responsible-use)
3.  [Learning Objectives](#3-learning-objectives)
4.  [Toolset](#4-toolset)
5.  [Practical Modules](#5-practical-modules)
    -   [W2-PM1 --- Kali Footprinting
        Toolkit](#w2-pm1--kali-footprinting-toolkit)
    -   [W2-PM2 --- Maltego Footprinting](#w2-pm3--maltego-footprinting)
    -   [W2-PM3 --- theHarvester
        Footprinting](#w2-pm4--theharvester-footprinting)
    -   [W2-PM4 --- Zenmap Network
        Scanning](#w2-pm4--zenmap-network-scanning)
6.  [Evidence Matrix](#6-evidence-matrix)
7.  [Security Observations](#7-security-observations)
8.  [Defensive Recommendations](#8-defensive-recommendations)
9.  [Key Takeaways](#9-key-takeaways)
10. [Repository Structure](#10-repository-structure)
11. [Final Submission Checklist](#11-final-submission-checklist)

------------------------------------------------------------------------

# 1. Project Snapshot

## 🎯 Purpose

Week 02 covers the reconnaissance stage of a cybersecurity assessment.
The practical workflow moves from collecting publicly available domain
information to understanding web and DNS exposure, visualising OSINT
relationships, gathering public host information, and discovering
devices on an authorised local network.

## 🧭 Completed Practical Modules

  -----------------------------------------------------------------------
  Module            Practical         Primary Focus     Status
  ----------------- ----------------- ----------------- -----------------
  **W2-PM1**        Kali Footprinting WHOIS, web        ✅ Completed
                    Toolkit           fingerprinting,   
                                      DNS and WAF       
                                      information       

  **W2-PM2**        Maltego           Visual OSINT and  ✅ Completed
                                      relationship      
                                      mapping           

  **W2-PM3**        theHarvester      Public host and   ✅ Completed
                                      information       
                                      harvesting        

  **W2-PM4**        Zenmap            Local host        ✅ Completed
                                      discovery and     
                                      topology          
  -----------------------------------------------------------------------

> **Note:** The GHDB/PM2 module is intentionally omitted from this
> version of the project documentation.

------------------------------------------------------------------------

# 2. Scope & Responsible Use

This project is intended for **educational cybersecurity training**.

The practical activities are limited to:

-   The target/domain assigned by the internship.
-   Publicly available information where the exercise is passive OSINT.
-   My own or explicitly authorised local network for Zenmap/Nmap
    discovery.
-   Systems and information for which testing or collection is
    permitted.

## 🚫 Out of Scope

The following activities are not part of this project:

-   Unauthorised access.
-   Credential theft or password attacks.
-   Exploitation of discovered vulnerabilities.
-   Denial-of-service activity.
-   Modification or deletion of data.
-   Accessing private accounts or restricted information.

> **Security note:** A hostname, IP address, email address, technology,
> or open service discovered during reconnaissance is an observation. It
> should not automatically be described as a confirmed vulnerability.

------------------------------------------------------------------------

# 3. Learning Objectives

Through these exercises, I aimed to:

1.  Understand the purpose and workflow of reconnaissance.
2.  Practise passive and authorised information gathering.
3.  Identify information exposed through DNS and web technologies.
4.  Understand how different reconnaissance tools reveal different parts
    of an infrastructure.
5.  Use Maltego to represent relationships between digital entities.
6.  Use theHarvester to collect publicly available hosts and related
    information.
7.  Use Zenmap/Nmap to discover active hosts on an authorised network.
8.  Record commands, observations and screenshots in a professional
    format.
9.  Distinguish between information exposure and a confirmed security
    vulnerability.
10. Understand why reducing unnecessary public exposure is important for
    security.

------------------------------------------------------------------------

# 4. Toolset

  -----------------------------------------------------------------------
  Tool                                Role in the Project
  ----------------------------------- -----------------------------------
  **Kali Linux**                      Security-testing environment used
                                      for command-line reconnaissance

  **WHOIS**                           Domain registration and nameserver
                                      information

  **WhatWeb**                         Web-server and technology
                                      fingerprinting

  **nslookup**                        DNS name resolution

  **curl**                            HTTP response/header inspection

  **Wafw00f**                         Web Application Firewall
                                      identification

  **DNSRecon**                        DNS record enumeration

  **Maltego**                         Graph-based OSINT and entity
                                      relationship analysis

  **theHarvester**                    Public host/email/subdomain
                                      collection

  **Zenmap / Nmap**                   Host discovery and network topology
                                      visualisation
  -----------------------------------------------------------------------

------------------------------------------------------------------------

# 5. Practical Modules

## W2-PM1 --- Kali Footprinting Toolkit

### Objective

The purpose of PM1 is to understand how several small reconnaissance
utilities can be combined to create a technical profile of a domain.

### Tools Used

-   WHOIS
-   WhatWeb
-   nslookup
-   curl
-   Wafw00f
-   DNSRecon

------------------------------------------------------------------------

### 5.1 WHOIS

**Command used:**

``` bash
whois networkwalks.com
```

**What I checked**

The WHOIS output was reviewed for publicly available registration
information, registrar details, registration dates and authoritative
nameservers.

**Evidence**



[PM1 - WHOIS]

<img width="1680" height="1009" alt="Screenshot 2026-08-19 at 2 26 57 PM" src="https://github.com/user-attachments/assets/a275b243-4d4d-4616-9ff4-0ba200fc3c23" />


------------------------------------------------------------------------

### 5.2 WhatWeb

**Command used:**

``` bash
whatweb networkwalks.com
```

**What I checked**

WhatWeb was used to identify technologies exposed by the website,
including web-server and application/platform indicators.

The captured result identified:

`192.232.216.135`

and reported Apache/WordPress-related technology information.

**Evidence**

`screenshots/pm1-whatweb.png`

[PM1 - WhatWeb](./screenshots/pm1-whatweb.png)

<img width="1680" height="1009" alt="Screenshot 2026-08-19 at 2 32 18 PM" src="https://github.com/user-attachments/assets/ad4bf683-6214-4d09-b06a-1103e59d4301" />


------------------------------------------------------------------------

### 5.3 nslookup

**Command used:**

``` bash
nslookup networkwalks.com
```

**Observation**

The DNS lookup returned:

`192.232.216.135`

This provided an independent DNS resolution result for the domain.

**Evidence**

`screenshots/pm1-nslookup.png`

[PM1 - nslookup](./screenshots/pm1-nslookup.png)

<img width="1680" height="1009" alt="Screenshot 2026-08-19 at 2 32 56 PM" src="https://github.com/user-attachments/assets/d5d2e955-8ad5-4e35-9033-f4f67a5cf86a" />


------------------------------------------------------------------------

### 5.4 curl

**Command used:**

``` bash
curl -I https://networkwalks.com
```

**What I checked**

The HTTP response headers were inspected for information such as HTTP
status, server information, security-related headers and
application-related response details.

The captured output returned an HTTP `200` response and exposed
technical header information including Apache and WordPress-related
links.

**Evidence**

`screenshots/pm1-curl.png`

[PM1 - curl](./screenshots/pm1-curl.png)

<img width="1680" height="519" alt="Screenshot 2026-08-19 at 2 38 25 PM" src="https://github.com/user-attachments/assets/71ef2fbf-4761-4cb5-bff0-35d05dbd60b2" />


------------------------------------------------------------------------

### 5.5 Wafw00f

**Command used:**

``` bash
wafw00f networkwalks.com
```

**Observation**

The captured result identified **ModSecurity (SpiderLabs)** as the web
application firewall protecting the site.

**Evidence**

`screenshots/pm1-wafw00f.png`

[PM1 - Wafw00f](./screenshots/pm1-wafw00f.png)


<img width="1680" height="1009" alt="Screenshot 2026-08-19 at 2 33 57 PM" src="https://github.com/user-attachments/assets/bafa213b-7666-4c94-b59c-4e370fd7a009" />
------------------------------------------------------------------------

### 5.6 DNSRecon

**Command used:**

``` bash
dnsrecon -d networkwalks.com
```

**What I checked**

DNSRecon was used to enumerate publicly available DNS information,
including:

-   SOA
-   NS
-   MX
-   TXT/SPF
-   SRV records

The captured output also showed cPanel autodiscover-related records.

**Evidence**

`screenshots/pm1-dnsrecon.png`

[PM1 - DNSRecon](./screenshots/pm1-dnsrecon.png)

<img width="1680" height="1009" alt="Screenshot 2026-08-19 at 2 36 52 PM" src="https://github.com/user-attachments/assets/b81515ba-770c-4a9b-a66b-a8afa7b3201a" />


------------------------------------------------------------------------

### PM1 Summary

PM1 demonstrated that different reconnaissance tools reveal different
parts of the same public-facing infrastructure. Registration
information, DNS records, web technologies, HTTP headers and WAF
information can be combined to create a broader reconnaissance picture.

------------------------------------------------------------------------

## W2-PM2<img width="1680" height="1009" alt="Screenshot 2026-08-19 at 2 26 57 PM" src="https://github.com/user-attachments/assets/82fd0ef2-70bd-4709-be88-5703e3ff59c9" />
 --- Maltego Footprinting

### Objective

The purpose of PM3 is to use Maltego as a visual OSINT platform and
understand how separate pieces of public information can be represented
as connected entities.

### Procedure

1.  Opened Maltego Desktop.
2.  Created a Domain entity.
3.  Entered the assigned domain information.
4.  Selected the available footprinting/OSINT transforms.
5.  Examined the resulting entities and relationships.
6.  Captured the graph and entity details as evidence.

### Evidence --- Screenshot 1

`screenshots/maltego1.png`

[PM2 - Maltego Setup] video+png



https://github.com/user-attachments/assets/ba6e740e-2123-4162-bc70-bc9f26f5bd9c



<img width="1634" height="973" alt="Screenshot 2026-08-19 at 6 06 48 PM" src="https://github.com/user-attachments/assets/91df6ef9-9ff6-4b3b-9356-db77aa751ebc" />


This screenshot shows the initial Maltego domain entity and the target
configuration.

### Evidence --- Screenshot 2

`screenshots/maltego2.png`

![PM2 - Maltego Graph Results](./screenshots/maltego2.png)

<img width="1680" height="996" alt="Screenshot 2026-08-19 at 6 09 20 PM" src="https://github.com/user-attachments/assets/efc26577-d15f-4f63-a369-941cdc3364a0" />


This screenshot shows the populated graph and transform output after the
analysis was performed.

### Observation

Maltego makes relationships easier to understand visually. Instead of
examining individual pieces of information separately, related domains,
email addresses, DNS information and infrastructure entities can be
represented as nodes and links.

### Security Lesson

A single public data point may appear harmless, but several related
pieces of information can reveal a much clearer picture of an
organisation's digital footprint.

------------------------------------------------------------------------

## W2-PM3 --- theHarvester Footprinting

### Objective

The purpose of PM4 is to understand how OSINT aggregation tools can
collect publicly available hosts and related information from configured
sources.

### Tool

**theHarvester**

### Initial Tool Check

The following command was used to view the available options:

``` bash
theHarvester -h
```

**Supporting Evidence**

`screenshots/theharvester-help.png`

![PM3 - theHarvester Help](./screenshots/theharvester-help.png)

<img width="1680" height="971" alt="Screenshot 2026-08-19 at 6 56 58 PM" src="https://github.com/user-attachments/assets/92d8ffaa-2976-471c-86ef-8553c8f20762" />


> This screenshot is supporting evidence. The main PM4 evidence is the
> actual harvesting result.

### Footprinting Command

The captured practical run used:

``` bash
theHarvester -d microsoft.com -l 1000 -b duckduckgo
```

### Observed Result

The captured output showed:

-   Target: `microsoft.com`
-   Search source: DuckDuckGo
-   IP addresses found: `0`
-   Emails found: `0`
-   People found: `0`
-   Hosts found: `27`

The output displayed a list of Microsoft-related hostnames.

### Main Evidence

`screenshots/theharvester-results.png`

![PM3 - theHarvester Results](./screenshots/theharvester-results.png)

<img width="1680" height="1013" alt="Screenshot 2026-08-19 at 6 57 31 PM" src="https://github.com/user-attachments/assets/6ddcfd01-8f46-48c6-900b-715e5b5f9eae" />


### Observation

The exercise demonstrates how an OSINT aggregation tool can collect host
information from publicly available search-engine data without requiring
direct exploitation of the target.

### Security Lesson

Publicly discoverable hostnames can provide useful information about an
organisation's external attack surface. Organisations should monitor
their public DNS and hostname footprint and remove unnecessary exposure
where possible.

------------------------------------------------------------------------

## W2-PM4 --- Zenmap Network Scanning

### Objective

PM5 is the essential network-discovery module. The purpose is to
identify active hosts on an authorised local network and understand how
those hosts can be represented visually.

> **Important:** Zenmap/Nmap scanning should only be performed against a
> network that I own or have explicit permission to test.

### Scan Performed

The supplied Zenmap evidence shows a Ping Scan using:

``` bash
nmap -sn 10.0.2.2
```

### Observation

The scan identified the target host as active and displayed its MAC
address information. The Zenmap host list also contained:

-   `10.0.0.1`
-   `10.0.2.2`
-   `192-232-216-135`

### Evidence --- Zenmap Scan

`screenshots/zenmap1.png`

![PM4 - Zenmap Scan](./screenshots/zenmap1.png)

<img width="1151" height="863" alt="Screenshot 2026-08-19 at 4 56 47 PM" src="https://github.com/user-attachments/assets/f02e05e6-e8f6-49ec-a6d2-305dc4f705ff" />


### Evidence --- Zenmap Topology

The topology view visually represents the discovered hosts and their
relationship to the local host.

`screenshots/zenmap2.png`

![PM4 - Zenmap Topology](./screenshots/zenmap2.png)




https://github.com/user-attachments/assets/e0d966da-f526-446d-9df7-093208d08fea







<img width="1151" height="863" alt="Screenshot 2026-08-19 at 5 00 41 PM" src="https://github.com/user-attachments/assets/3ac60d69-38c3-4195-87cb-28817e81771a" />


### Observation

The topology view provides a faster visual understanding of the hosts
discovered during network reconnaissance.

### Security Lesson

Network discovery is useful for defensive inventory as well as security
assessment. An organisation should know which devices are connected to
its network, whether those devices are expected, and what services they
expose.

------------------------------------------------------------------------

# 6. Evidence Matrix

The following matrix provides a quick verification of the evidence
expected in the repository.

  Module   Evidence File                Purpose                     Status
  -------- ---------------------------- --------------------------- --------
  PM1      `pm1-whois.png`              WHOIS information           ✅
  PM1      `pm1-whatweb.png`            Technology fingerprinting   ✅
  PM1      `pm1-nslookup.png`           DNS resolution              ✅
  PM1      `pm1-curl.png`               HTTP headers                ✅
  PM1      `pm1-wafw00f.png`            WAF identification          ✅
  PM1      `pm1-dnsrecon.png`           DNS enumeration             ✅
  PM2      `maltego1.png`               Initial Maltego setup       ✅
  PM2      `maltego2.png`               Populated OSINT graph       ✅
  PM3      `theharvester-help.png`      Tool/help evidence          ✅
  PM3      `theharvester-results.png`   Main harvesting evidence    ✅
  PM4      `zenmap1.png`                Network discovery           ✅
  PM4      `zenmap2.png`                Network topology            ✅

------------------------------------------------------------------------

# 7. Security Observations

  -----------------------------------------------------------------------
  Observation                         Security Significance
  ----------------------------------- -----------------------------------
  Domain registration information is  Helps build an initial profile of a
  publicly available                  domain

  DNS records reveal infrastructure   Can expose mail, hosting and
  relationships                       service information

  Web technology can sometimes be     Helps identify technologies that
  fingerprinted                       require patching

  HTTP headers may disclose           Unnecessary information can
  implementation details              increase reconnaissance value

  OSINT can connect otherwise         Relationships may reveal more than
  separate data points                individual records

  Public hostnames can be collected   Increases visibility of an
  automatically                       organisation's external footprint

  Local network discovery reveals     Useful for asset inventory and
  active devices                      defensive monitoring
  -----------------------------------------------------------------------

> These observations describe reconnaissance exposure. They should not
> be interpreted as confirmed exploitable vulnerabilities unless a
> separate authorised security test proves exploitation is possible.

------------------------------------------------------------------------

# 8. Defensive Recommendations

Based on the lessons from the practical modules:

1.  **Reduce unnecessary information disclosure** --- avoid exposing
    software versions and infrastructure details when they are not
    required.
2.  **Keep web applications updated** --- patch CMS platforms, plugins
    and supporting software regularly.
3.  **Review HTTP headers** --- remove unnecessary response information
    where possible.
4.  **Audit DNS records** --- remove obsolete or unnecessary records.
5.  **Review the organisation's OSINT footprint** --- identify
    information that can be combined by an external observer.
6.  **Protect publicly accessible devices** --- especially cameras,
    routers, management interfaces and IoT systems.
7.  **Maintain an accurate network inventory** --- investigate
    unexpected devices promptly.
8.  **Secure administrative interfaces** --- restrict management
    services and use strong authentication.
9.  **Monitor external exposure regularly** --- periodically reassess
    public-facing infrastructure.
10. **Stay within authorised scope** --- never apply reconnaissance or
    scanning techniques to systems without permission.

------------------------------------------------------------------------

# 9. Key Takeaways

### 🔎 Reconnaissance comes first

A security assessment can reveal significant information before
exploitation is attempted.

### 🧩 Small data points can connect

WHOIS, DNS, web technologies, hostnames and OSINT relationships can
collectively create a detailed external footprint.

### 🌐 Public exposure matters

Information that is publicly available may still provide useful
intelligence to an attacker.

### 🗺️ Network visibility is important

Zenmap demonstrates why organisations need an accurate understanding of
the devices present on their networks.

### 🛡️ Reconnaissance also supports defence

The same techniques can be used responsibly to identify unnecessary
exposure and improve an organisation's security posture.

------------------------------------------------------------------------

# 10. Repository Structure

The recommended repository structure is:

``` text
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

------------------------------------------------------------------------

# 11. Final Submission Checklist

Before submitting the GitHub repository:

-   [ ] README opens correctly on GitHub.
-   [ ] All screenshot filenames match the Markdown image paths.
-   [ ] Every screenshot is my own captured evidence.
-   [ ] PM1 contains all six required tool screenshots.
-   [ ] PM2 contains both Maltego screenshots.
-   [ ] PM3 contains the actual theHarvester result screenshot.
-   [ ] PM4 contains the Zenmap scan and topology screenshots.
-   [ ] No sample screenshot is presented as personal work.
-   [ ] No unsupported findings have been added.
-   [ ] Target/scope information is accurate.
-   [ ] The final report contains the same evidence as the GitHub
    repository.
-   [ ] Personal information that does not need to be public has been
    removed.
-   [ ] The repository does not contain passwords, API keys, tokens or
    other secrets.

------------------------------------------------------------------------

## 📌 Final Note

This README is structured as an original Week 02 practical project
document. It focuses on the completed reconnaissance modules and ties
each practical section to its corresponding evidence.

**Week 02 --- Reconnaissance, OSINT & Network Discovery**

*Cybersecurity Internship Practical Project*
