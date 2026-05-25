
---
# Practical Guide for Understanding and Using a Honeypot with PentBox

A honeypot is a security mechanism designed to imitate a real system or service in order to attract attackers and monitor their activities. It helps security professionals study attack patterns, intrusion techniques, and malicious behavior in a controlled environment. This practical guide demonstrates how to create and monitor a basic honeypot using PentBox.

## Objective:

To understand the working of a honeypot and deploy a basic honeypot using PentBox for intrusion monitoring.

## Prerequisites:

* A Linux system (Kali Linux, Ubuntu, or any penetration testing environment)
* Internet connectivity
* Git installed
* Basic understanding of Linux terminal commands and networking concepts

---

## Steps:

### 1. Clone the PentBox Repository:

**Bash**

```bash
git clone https://github.com/technicaldada/pentbox
cd pentbox
```

**Explanation:**
This command downloads the PentBox toolkit from GitHub and navigates into its directory.

---

### 2. Start PentBox:

**Bash**

```bash
./pentbox.rb
```

**Explanation:**
This command launches the PentBox command-line interface.

---

## Using PentBox Honeypot:

After launching PentBox, a CLI menu appears.

### Step 3: Navigate to Network Tools

Choose:

```text
2 → Network Tools
```

Then select:

```text
Honeypot
```

**Explanation:**
This opens the honeypot module, allowing you to simulate a vulnerable service.

---

## Honeypot Configuration Options:

PentBox provides two configuration modes:

```text
1 → Fast Configuration
2 → Manual Configuration
```

---

# Option 1: Fast Configuration

Choose:

```text
1
```

### What Happens:

* PentBox automatically starts the honeypot.
* By default, it listens on **Port 80 (HTTP)**.

**Explanation:**
Fast configuration quickly deploys a web-based honeypot using default settings.

---

### Step 4: Find Your System IP Address

**Bash**

```bash
ip a
```

**Explanation:**
Displays all network interfaces and IP addresses of your machine.

---

### Step 5: Access the Honeypot

Copy your system's IP address and paste it into a web browser:

```text
http://<your-ip-address>
```

Example:

```text
http://192.168.1.10
```

**Explanation:**
When someone visits this IP address, PentBox captures the connection details.

---

### Output:

The terminal displays browser/client information such as:

* Source IP Address
* Browser Details
* Request Information
* Connection Time

**Explanation:**
This information helps analyze potential intruders and connection attempts.

---

# Option 2: Manual Configuration

Choose:

```text
2
```

PentBox will ask for custom settings.

---

### Step 4: Enter Port Number

Example:

```text
8080
```

**Explanation:**
Allows you to run the honeypot on any desired port.

---

### Step 5: Enter a Fake Message

Example:

```text
Access Denied! Unauthorized access detected.
```

**Explanation:**
This message will be shown to anyone attempting to connect.

---

### Step 6: Save Logs

Prompt:

```text
Save log? (Y/n)
```

Choose:

```text
Y
```

**Explanation:**
Stores intrusion attempts for later analysis.

---

### Step 7: Enable Beep Alert

Prompt:

```text
Beep sound for intrusion? (Y/n)
```

Choose:

```text
Y
```

**Explanation:**
Produces an audible alert whenever an intrusion attempt occurs.

---

## Example Scenario:

Suppose you configure the honeypot on port **8080** with logging enabled.

* An attacker tries to connect to:

```text
http://192.168.1.10:8080
```

PentBox captures:

* Source IP address
* Browser information
* Timestamp
* Connection request details

These logs can be used to study attacker behavior.

---

## Explanation of Functionality:

A honeypot works by:

### Service Emulation

It imitates a real network service such as HTTP or FTP.

### Intrusion Monitoring

It records all incoming connection attempts.

### Attack Analysis

It helps identify attacker tools, IP addresses, and techniques.

### Alerting

It can notify administrators in real-time when an intrusion occurs.

---

## Applications of Honeypots:

* Network intrusion detection
* Malware behavior analysis
* Threat intelligence gathering
* Security research and training
* Incident response investigation

