---
tags:
  - cybercrime
  - forensics
  - kali-linux
  - home
cssclasses:
  - home
---

# 🔍 Introduction to Cyber Crime Investigation

> A **cybercrime investigator** focuses on gathering evidence from digital systems to prosecute internet-based criminal activities. These crimes often leverage the internet as the primary attack vector. Investigators analyze digital evidence, recover files, and create reports for use in court.

---

## 👤 Responsibilities of Cybercrime Investigators

- Analyzing compromised computer systems and networks
- Recovering damaged or deleted data
- Gathering and preserving evidence for legal proceedings
- Reconstructing cyberattacks
- Preparing detailed technical reports and expert testimony
- Training law enforcement on cybersecurity topics

---

## 🧠 Skills & Experience

### Core Skills

| Area | Details |
|------|---------|
| Digital Systems | Knowledge of mobile OS, hardware, and system architecture |
| Forensics | Proficiency in cyber forensics tools and malware analysis |
| Programming | Python, PHP, Java |
| Data & Security | Metadata analysis, password cracking, encryption |
| Vulnerability Assessment | Software, networks, and device weaknesses |

### Tools & Methods

- Forensic software for evidence collection
- Metadata cleansing
- Reverse engineering of malware and exploit methods

---

## 🚨 Types of Cyber Crimes

### 1. 💻 Computer Hacking
Involves unauthorized modification of computer systems.

- **Ransomware** — Data held hostage until a ransom is paid
- **Phishing** — Deceptive emails trick users into revealing sensitive information or downloading malware

### 2. ©️ Copyright Infringement
Theft of intellectual property (movies, music, software) often via file-sharing platforms, causing monetary losses.

### 3. 👁️ Cyber Stalking
Persistent online harassment or surveillance, often targeting women. Distinct from legitimate online research such as employer background checks.

### 4. 🌊 DDoS Attacks
Distributed Denial-of-Service attacks overwhelm servers with data traffic, disrupting services.

### 5. 💰 Extortion

- **Ransomware** — Demands payment for restoring access to encrypted files
- **Cryptojacking** — Unauthorized cryptocurrency mining using victim systems

### 6. 🃏 Fraud
Includes credit/debit card fraud and identity theft, where personal information is exploited for financial gain.

### 7. 🪪 Identity Theft
Unauthorized use of personal data to commit financial fraud or other crimes.

### 8. 🧒 Online Predators
Targets minors via social media to exploit or groom them for malicious purposes.

### 9. 🔓 Personal Data Breaches
Hackers steal sensitive user data through vulnerabilities, weak passwords, or malware.

---

## 🛡️ Preventing Cyber Crimes

### Best Practices
- Use firewalls and antivirus software
- Regularly update software to patch vulnerabilities
- Educate users on phishing and other threats
- Implement strong password policies

### Managing Social Media
- Adjust privacy settings to limit exposure
- Avoid oversharing personal information

### Parental Guidance
- Educate children about online dangers
- Monitor their online activities responsibly

---

## 🐉 Ethical Hacking & Kali Linux

**Kali Linux** is a Debian-based distribution tailored for penetration testing and security analysis. It includes over 600 pre-installed tools for network analysis, vulnerability assessment, and password recovery.

### File System Structure

| Path | Purpose |
|------|---------|
| `/bin` | System binaries |
| `/root` | Root user home directory |
| `/usr/share` | Tools like Nmap and Metasploit |
| `/var` | Logs and website data |

### Common Commands

| Command | Description |
|---------|-------------|
| `pwd` | Print working directory |
| `cd` | Change directory |
| `ls` | List directory contents |
| `chmod` | Modify file permissions |
| `ifconfig` | Display network configuration |

### File Permissions

File permissions are divided into three categories:

1. **Owner** — What the file owner can do
2. **Group** — Actions allowed for users in the same group
3. **Others** — Actions for all other users

Each permission is represented by a character:

| Symbol | Name | Meaning |
|--------|------|---------|
| `r` | Read | View or read the file's contents |
| `w` | Write | Modify or delete the file |
| `x` | Execute | Run the file or access a directory |

### Permission String Structure

Permissions are displayed as a 10-character string, e.g., `-rwxr-xr--`:

```
- rwx r-x r--
│ │   │   └── Others
│ │   └────── Group
│ └────────── Owner
└──────────── File type (- = file, d = directory)
```

### Numeric Representation

| Value | Permission |
|-------|-----------|
| `4` | Read (r) |
| `2` | Write (w) |
| `1` | Execute (x) |

**Examples:**

| Number | Permissions | Meaning |
|--------|-------------|---------|
| `7` | `rwx` | Full permissions |
| `6` | `rw-` | Read and write |
| `5` | `r-x` | Read and execute |

### `chmod` Examples

```bash
chmod 764 filename     # Owner: rwx (7), Group: rw- (6), Others: r-- (4)
chmod u+x filename     # Add execute for owner
chmod g-w filename     # Remove write for group
```

### Special Permissions

| Permission | Symbol | Description |
|------------|--------|-------------|
| Setuid | `s` | Execute file with owner's privileges |
| Setgid | `s` | Apply group permissions to new files in directory |
| Sticky Bit | `t` | Only file owner can delete files in directory |

---

## ⚙️ Advanced Linux Techniques

### Shell Scripting
Shell scripts automate tasks by storing sequences of commands in `.sh` files.

```bash
chmod +x script.sh    # Make the script executable
```

### Process Management

| Command | Action |
|---------|--------|
| `Ctrl + C` | Stop a process |
| `Ctrl + Z` | Suspend a process |
| `nohup` | Prevent process termination after logout |

### Changing Ownership & Groups

```bash
chown username filename     # Change file ownership
chgrp groupname filename    # Change file group
```

---

## 🔧 Cybersecurity Utilities

### Hostname Configuration

```bash
hostnamectl set-hostname newname
```

### FTP Setup

- Install `vsftpd` for file sharing
- Configure `/etc/vsftpd.conf` for user-specific access

### SSH Setup

```bash
service ssh start    # Enable SSH on server
ssh user@host        # Connect from client (or use Putty)
```

---

## 📋 Practical List

| No. | Link | No. | Link | No. | Link |
|-----|------|-----|------|-----|------|
| 1  | [Practical 1](Practical%201.md)   | 26 | [practical 26](practical%2026.md) | 51 | [practical 51](practical%2051.md) |
| 2  | [practical 2](practical%202.md)   | 27 | [practical 27](practical%2027.md) | 52 | [practical 52](practical%2052.md) |
| 3  | [practical 3](practical%203.md)   | 28 | [practical 28](practical%2028.md) | 53 | [practical 53](practical%2053.md) |
| 4  | [practical 4](practical%204.md)   | 29 | [practical 29](practical%2029.md) | 54 | [practical 54](practical%2054.md) |
| 5  | [practical 5](practical%205.md)   | 30 | [practical 30](practical%2030.md) | 55 | —                                 |
| 6  | [practical 6](practical%206.md)   | 31 | [practical 31](practical%2031.md) | 56 | [practical 56](practical%2056.md) |
| 7  | [practical 7](practical%207.md)   | 32 | [practical 32](practical%2032.md) | 57 | [practical 57](practical%2057.md) |
| 8  | [practical 8](practical%208.md)   | 33 | [practical 33](practical%2033.md) | 58 | [practical 58](practical%2058.md) |
| 9  | [practical 9](practical%209.md)   | 34 | [practical 34](practical%2034.md) | 59 | [practical 59](practical%2059.md) |
| 10 | [practical 10](practical%2010.md) | 35 | [practical 35](practical%2035.md) | 60 | [practical 60](practical%2060.md) |
| 11 | [practical 11](practical%2011.md) | 36 | [practical 36](practical%2036.md) | 61 | —                                 |
| 12 | [practical 12](practical%2012.md) | 37 | [practical 37](practical%2037.md) | 62 | —                                 |
| 13 | [practical 13](practical%2013.md) | 38 | [practical 38](practical%2038.md) | 63 | —                                 |
| 14 | [practical 14](practical%2014.md) | 39 | [practical 39](practical%2039.md) | 64 | —                                 |
| 15 | [practical 15](practical%2015.md) | 40 | [practical 40](practical%2040.md) | 65 | —                                 |
| 16 | [practical 16](practical%2016.md) | 41 | [practical 41](practical%2041.md) |    |                                   |
| 17 | [practical 17](practical%2017.md) | 42 | [practical 42](practical%2042.md) |    |                                   |
| 18 | [practical 18](practical%2018.md) | 43 | [practical 43](practical%2043.md) |    |                                   |
| 19 | [practical 19](practical%2019.md) | 44 | [practical 44](practical%2044.md) |    |                                   |
| 20 | [practical 20](practical%2020.md) | 45 | [practical 45](practical%2045.md) |    |                                   |
| 21 | [practical 21](practical%2021.md) | 46 | [practical 46](practical%2046.md) |    |                                   |
| 22 | [practical 22](practical%2022.md) | 47 | [practical 47](practical%2047.md) |    |                                   |
| 23 | [practical 23](practical%2023.md) | 48 | [practical 48](practical%2048.md) |    |                                   |
| 24 | [practical 24](practical%2024.md) | 49 | [practical 49](practical%2049.md) |    |                                   |
| 25 | [practical 25](practical%2025.md) | 50 | [practical 50](practical%2050.md) |    |                                   |
