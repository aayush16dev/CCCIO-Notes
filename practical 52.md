
---

# Practical Guide for Using LittleBrother in Kali Linux

Open Source Intelligence (OSINT) tools are widely used in cybersecurity and digital investigations to gather publicly available information about IP addresses, domains, hashes, usernames, and other digital artifacts. This practical demonstrates the installation and usage of LittleBrother on Kali Linux.

---

# Objective

To install and use LittleBrother for IP lookup and hash analysis in a controlled cybersecurity lab environment.

---

# Prerequisites

* Kali Linux or any Debian-based Linux distribution
* Internet connectivity
* Git installed
* Python 3 installed
* Basic knowledge of Linux commands

---

# Introduction to LittleBrother

LittleBrother is a Python-based information gathering and OSINT toolkit that provides multiple modules for:

* IP lookup
* Username analysis
* Information gathering
* Hash analysis
* Reconnaissance tasks

The tool is mainly used for cybersecurity education and digital investigation demonstrations.

---

# Step 1: Clone the Repository

Open the terminal and run:

**Bash**

```bash id="42zw3z"
git clone https://github.com/lulz3xploit/LittleBrother.git
```

**Explanation:**
Downloads the LittleBrother project from GitHub.

---

# Step 2: Navigate into the Directory

**Bash**

```bash id="2k7x0z"
cd LittleBrother
```

---

# Step 3: View Project Files

**Bash**

```bash id="7rmlb5"
ls
```

Example output:

```text id="r7pqtx"
core
Dockerfile
lib
LittleBrother.py
__pycache__
README.md
requirements.txt
settings.py
txt
Watched
```

**Explanation:**
Displays the project structure and available files.

---

# Step 4: Give Execution Permissions

**Bash**

```bash id="d6kzyz"
chmod +x 777 *
```

**Explanation:**
Provides execution permissions to project files.

---

# Step 5: Install Dependencies

**Bash**

```bash id="7rfh7u"
pip3 install -r requirements.txt
```

**Explanation:**
Installs required Python libraries used by the application.

---

# Step 6: Run LittleBrother

**Bash**

```bash id="y4f8ys"
python3 LittleBrother.py
```

**Explanation:**
Starts the LittleBrother toolkit interface.

---

# Using the Lookup Module

After launching the tool, multiple menu options appear.

Select:

```text id="cij7n8"
1 → Lookup
```

---

# IP Lookup Demonstration

Inside the Lookup menu, choose:

```text id="t6ocmj"
IP Lookup
```

The program prompts for an IP address.

Example:

```text id="0j4x4o"
8.8.8.8
```

---

# Example Output

The tool may display information such as:

* ISP
* Organization
* Country
* Region
* Ville
* Code Postal
* Localisation
* Maps

**Explanation:**
The lookup module performs IP geolocation and network information gathering.

---

# Hash Analysis Module

LittleBrother also provides hash-related utilities.
Select another option from the main menu:

```text id="py0d20"
Hash Decrypter
```

---

# Using Hash Decrypter

Enter a hash value when prompted.

Example:

```text id="xvfjlwm"
5f4dcc3b5aa765d61d8327deb882cf99
```

The tool attempts to identify or recover the original plaintext using supported lookup or cracking techniques.

---

# Example Result

```text id="1k7bqq"
password
```

---
# Applications of LittleBrother

* OSINT investigations
* Network reconnaissance
* IP geolocation analysis
* Cybersecurity training
* Hash analysis and education
* Digital forensics learning

---

---
