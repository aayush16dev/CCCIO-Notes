
---
---

# **Practical Guide for Using Tor-IP-Changer**

## Objective

The objective of this practical is to automatically change the Tor exit node IP address using the **Tor-IP-Changer** script in Kali Linux.

---

## Pre-requisites

1. **Kali Linux System**: A working Kali Linux installation.

2. **Internet Connectivity**: Required for downloading packages and connecting to the Tor network.

3. **Tor Service**: Must be installed and running.

4. **Terminal Access**: Required to execute commands.

5. **Basic Linux Knowledge**: Familiarity with Linux commands and networking concepts.

---

# Commands as Steps

## 1. Update and Upgrade the System

```bash id="u4x9zr"
apt update

apt upgrade -y
```

### Explanation

Updates the package repository and upgrades installed packages to their latest versions.

---

## 2. Install Python3

```bash id="m8c2vd"
apt install -y python3
```

### Explanation

Installs Python3, which is required to execute the Tor-IP-Changer script.

---

## 3. Clone the Tor-IP-Changer Repository

```bash id="n7q1kw"
git clone https://github.com/isPique/Tor-IP-Changer.git

cd Tor-IP-Changer
```

### Explanation

Downloads the Tor-IP-Changer project from GitHub and navigates into the project directory.

---

## 4. Make the Script Executable

```bash id="r5t8hy"
chmod +x tor-ip-changer.py
```

### Explanation

Grants executable permissions to the script file.

---

## 5. Run the Script

```bash id="k3v6pm"
./tor-ip-changer.py
```

### Explanation

Executes the Tor-IP-Changer script to request a new Tor circuit and change the Tor exit node IP address.

---

## 6. Verify IP Address Change

### Method 1

Visit websites such as:

```text id="p9d4ln"
https://whatismyipaddress.com
```

Check the IP address before and after running the script.

### Explanation

A different IP address confirms that the Tor exit node has changed successfully.

---

# Explanation of the Script Functionality

The `tor-ip-changer.py` script uses the **Stem** Python library to communicate with the Tor control port.

When executed:

* The script connects to the Tor control service.

* It requests a new Tor circuit.

* Tor assigns a different exit node.

* The external IP address changes accordingly.

This process improves anonymity and allows testing from multiple network identities.

---

# Additional Testing and Information

## 1. Start Tor Service

```bash id="x6m2qa"
systemctl start tor
```

### Explanation

Starts the Tor service required for IP rotation.

---

## 2. Automate IP Changes Using Cron

```bash id="f1w7zk"
crontab -e
```

Add the following line:

```bash id="d3r9uy"
0 * * * * /path/to/Tor-IP-Changer/tor-ip-changer.py
```

### Explanation

Automatically executes the script every hour to rotate the Tor exit node IP address.

---

## 3. Check Tor Connection Status

```bash id="q5p8te"
curl -s https://check.torproject.org/ | grep -i "Congratulations"
```

### Explanation

Verifies whether the current connection is successfully routed through the Tor network.

---

# Additional Notes

* The script changes the Tor exit node automatically using Tor control commands.

* The exit node location is randomly assigned by the Tor network.

* Ensure the Tor service is active before running the script.

* Tor logs can be checked in:

```text id="a7v5md"
/var/log/tor/
```

* Use this tool only for ethical, educational, and authorized security testing purposes.

---

