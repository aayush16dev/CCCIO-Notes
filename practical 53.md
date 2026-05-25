
---

# Practical Guide for Device Fingerprinting and Web Panel Analysis Using Storm-Breaker

Device fingerprinting is a technique used in cybersecurity to identify devices based on browser, operating system, hardware, and network characteristics. This practical demonstrates the installation and local deployment of Storm-Breaker in a controlled lab environment to study web-based device information gathering, secure tunneling, and browser fingerprint analysis.

## Objective:

To understand web-based device fingerprinting, local web panel deployment, and secure tunneling in a cybersecurity lab environment.

## Prerequisites:

* Kali Linux or any Debian-based Linux distribution
* Internet connectivity
* Basic knowledge of Linux commands
* Git installed
* Python 3 installed
* PHP installed
* An ngrok account

---

## About Storm-Breaker

Storm-Breaker is a Python and PHP based web application designed for browser-based device information collection and panel-based monitoring.

### Supported Platform:

* Linux

### Programming Languages Used:

* Python 3.x
* PHP 7.4+

---

## Key Features (Lab Demonstration)

In a controlled environment, Storm-Breaker can demonstrate collection of browser-provided metadata such as:

* Device information
* Browser information
* Operating system details
* Screen resolution
* CPU information
* Time zone detection
* Language preferences
* Network IP information

### Updated Features

The latest version includes:

* Web-based administration panel
* Downloadable logs
* Clear log functionality
* Start/Stop listener support
* Improved templates
* Optimized graphical interface
* Support for localhost and personal hosting

---

## Dependencies

The tool requires:

* Python
* PHP
* Git
* ngrok

---

## Platforms Tested

According to project documentation:

* Kali Linux 2022
* macOS Big Sur
* Android (Termux)
* Personal hosting environments

---

# Installation Steps

## Step 1: Clone the Repository

**Bash**

```bash
git clone https://github.com/ultrasecurity/Storm-Breaker
cd Storm-Breaker
```

**Explanation:**
Downloads the project files from GitHub.

---

## Step 2: View Project Files

**Bash**

```bash
ls
```

Example output:

```text
install.sh
modules
README.md
requirements.txt
Settings.json
storm-web
st.py
```

---

## Step 3: Run Installation Script

**Bash**

```bash
sudo bash install.sh
```

**Explanation:**
Installs required dependencies.

---

## Step 4: Install Python Requirements

**Bash**

```bash
sudo python3 -m pip install -r requirements.txt
```

**Explanation:**
Installs required Python modules.

---

## Step 5: Launch the Application

**Bash**

```bash
sudo python3 st.py
```

Example output:

```text
[+] Web Panel Link : http://localhost:2525
```

**Explanation:**
Starts the local administration panel on port **2525**.

---

# Secure Tunnel Configuration

To access the panel remotely for testing:

## Install ngrok

**Bash**

```bash
curl -sSL https://ngrok-agent.s3.amazonaws.com/ngrok.asc \
| sudo tee /etc/apt/trusted.gpg.d/ngrok.asc >/dev/null \
&& echo "deb https://ngrok-agent.s3.amazonaws.com bookworm main" \
| sudo tee /etc/apt/sources.list.d/ngrok.list \
&& sudo apt update \
&& sudo apt install ngrok
```

---

## Authenticate ngrok

**Bash**

```bash
ngrok config add-authtoken <your-auth-token>
```

---

## Create Tunnel

**Bash**

```bash
ngrok http 2525
```

**Explanation:**
Creates a secure public tunnel to the local web application.

---

## Access the Panel

Open:

```text
http://localhost:2525
```

or use the generated ngrok forwarding URL.

---

# Default Panel Credentials

By default:

```text
Username : admin
Password : admin
```

These credentials can be modified in the configuration files for lab security.

---

# Sample Device Fingerprinting Output

When accessed in a controlled test environment, the panel may display browser-provided metadata such as:

```text
IP Address        : [Lab Test IP]
Operating System  : Linux
Architecture      : x86_64
Browser           : Firefox
Browser Version   : 140.0
CPU Architecture  : amd64
Screen Resolution : 1758 x 808
Time Zone         : Eastern Daylight Time
Language          : en-US
CPU Cores         : 4
```

---

## Information Collected

### Network Information

* Public IP address

### System Information

* Operating system
* CPU architecture
* Number of processor cores

### Browser Information

* Browser name
* Browser version
* Language preferences

### Display Information

* Screen resolution

### Regional Information

* Time zone

---

## Applications in Cybersecurity

This practical helps students understand:

* Browser fingerprinting
* Web metadata collection
* Secure tunneling
* Web-based monitoring dashboards
* Security awareness and privacy risks

---

## Conclusion

Using Storm-Breaker, Python, and ngrok, cybersecurity students can study how web applications collect browser metadata, analyze device fingerprints, and understand privacy implications in a controlled lab environment.
