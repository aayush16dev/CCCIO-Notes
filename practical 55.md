
---
# Practical Guide for Using Maryam in Kali Linux

Open Source Intelligence (OSINT) frameworks are used in cybersecurity investigations to gather publicly available information about domains, websites, DNS records, and online infrastructure. This practical demonstrates the installation and usage of Maryam in Kali Linux for DNS brute forcing and web crawling activities in a controlled lab environment.

---

# Objective

To understand the usage of the Maryam OSINT framework for DNS enumeration and website crawling.

---

# Prerequisites

* Kali Linux or any Debian-based Linux distribution
* Internet connectivity
* Basic understanding of Linux commands
* Basic knowledge of DNS and web technologies

---

# Introduction to Maryam

Maryam is a modular OSINT framework designed for cybersecurity investigations and reconnaissance.

### Features of Maryam

* DNS reconnaissance
* Website crawling
* Search engine analysis
* Metadata gathering
* Threat intelligence collection
* Information enumeration

---

# Step 1: Install Maryam

Open the terminal and run:

**Bash**

```bash id="ec1tyn"
sudo apt install maryam -y
```

**Explanation:**
Installs the Maryam framework from the Linux repositories.

---

# Step 2: Launch Maryam

**Bash**

```bash id="g1h4hr"
maryam
```

**Explanation:**
Starts the Maryam interactive OSINT console.

---

# Step 3: Display Available Workspaces

Inside the Maryam console, run:

```text id="g6fljlwm"
show workspaces
```

**Explanation:**
Displays all available workspaces used to organize investigation data.

---

# Step 4: Create a New Workspace

To create a workspace:

```text id="qlt1d0"
workspaces add aayush
```

**Explanation:**
Creates a new workspace named `aayush`.

---

# Step 5: Select an Existing Workspace

If the workspace already exists:

```text id="qgxz2n"
workspaces select aayush
```

**Explanation:**
Loads the selected workspace for storing investigation results.

---

# DNS Brute Force Enumeration

DNS brute forcing attempts to discover subdomains associated with a target domain.

# Step 6: Run DNS Brute Force

Command:

```text id="jlwm4m"
dnsbrute -d google.com -t 50
```

### Parameters

| Parameter | Meaning           |
| --------- | ----------------- |
| `-d`      | Target domain     |
| `-t 50`   | Number of threads |

**Explanation:**
Attempts to discover publicly available subdomains associated with the target domain.

---

# Example Output

The tool may identify subdomains such as:

```text id="utgqqn"
mail.google.com
maps.google.com
drive.google.com
accounts.google.com
```

---

# Web Crawling

A web crawler automatically scans and indexes pages from a website.

# Step 7: Run Website Crawler
Command:

```text id="3kvx8f"
crawler -d geeksforgeeks.org
```

**Explanation:**
Crawls the target website and gathers publicly accessible links and web resources.

---
# Information Gathered During Crawling

The crawler may collect:
* Internal links
* External links
* Page titles
* Website structure
* Public resources
* Metadata
---
# Applications of Maryam

* OSINT investigations
* DNS enumeration
* Web reconnaissance
* Threat intelligence
* Website mapping
* Cybersecurity research
* Security auditing

---
# Important Notes
* Use only on authorized systems and domains.
* Respect website terms of service.
* Perform testing in controlled environments.
* Unauthorized reconnaissance may violate laws or policies.

---

# Explanation of Functionality

### Maryam

Provides modular OSINT and reconnaissance tools.
### DNS Brute Force
Attempts to identify public subdomains.
### Web Crawler
Maps website content and structure.
### Workspaces
Organize investigation data and results.

---

