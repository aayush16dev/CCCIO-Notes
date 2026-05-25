
---
# **Practical Guide for Using Kalitorify**

## Objective

The objective of this practical is to anonymize all network traffic originating from a Kali Linux system by routing it through the Tor network using **Kalitorify**.

---

## Pre-requisites

1. **Kali Linux System**: A working Kali Linux installation.

2. **Internet Connectivity**: Required for downloading packages and connecting to the Tor network.

3. **Basic Linux Knowledge**: Familiarity with terminal commands and networking concepts.

4. **Terminal Access**: Needed to execute commands.

---

# Commands as Steps

## 1. Update and Upgrade the System

```bash id="x7m2qa"
apt update

apt upgrade -y
```

### Explanation

Updates package repositories and upgrades installed packages to their latest versions.

---

## 2. Install Dependencies

```bash id="p4v8tk"
apt install -y tor obfsproxy
```

### Explanation

Installs the required dependencies:

* `tor` provides anonymous routing through the Tor network.

* `obfsproxy` helps obfuscate Tor traffic to make detection more difficult.

---

## 3. Install Git

```bash id="n5u1dy"
apt install -y git
```

### Explanation

Installs Git, which is required to clone the Kalitorify repository.

---

## 4. Clone the Kalitorify Repository

```bash id="r2k7wp"
git clone https://github.com/brainfucksec/kalitorify.git

cd kalitorify
```

### Explanation

Downloads the Kalitorify project from GitHub and navigates into the project directory.

---

## 5. Install Kalitorify

```bash id="m8q4zc"
./install.sh
```

### Explanation

Executes the Kalitorify installation script to configure required files and settings.

---

## 6. Start Kalitorify

```bash id="t6n9xr"
kalitorify --tor
```

### Explanation

Starts transparent proxying through the Tor network.

Kalitorify configures `iptables` rules to redirect all network traffic through Tor.

---

## 7. Verify Tor Connection

### Method 1: Browser Verification

Open the browser and visit:

```text id="w1f5mv"
https://whatismyipaddress.com/
```

### Explanation

The displayed public IP address should change and reflect a Tor exit node.

---

### Method 2: Verify Using Curl

```bash id="k3p8yu"
curl -s https://check.torproject.org/ | grep -i "Congratulations"
```

### Explanation

Checks whether the connection is successfully routed through the Tor network.

If successful, a “Congratulations” message will appear.

---

## 8. Check Kalitorify Status

```bash id="v9r2kn"
kalitorify --status
```

### Explanation

Displays the current status of Kalitorify and related services.

---

## 9. Restart Tor Service and Change IP Address

```bash id="d7x4qm"
kalitorify --restart
```

### Explanation

Restarts the Tor service and generates a new Tor exit node IP address.

---

## 10. Display Current Public IP Address

```bash id="q5m1tc"
kalitorify --ipinfo
```

### Explanation

Displays the current public IP address being used through the Tor network.

---

## 11. Return to Clearnet

```bash id="u8n6py"
kalitorify --clearnet
```

### Explanation

Stops transparent proxying and restores the normal network configuration.

---

## 12. View Help Menu

```bash id="f2w9ka"
kalitorify --help
```

### Explanation

Displays all available Kalitorify commands and options.

---

# Commands List

| Command            | Description                          |
| ------------------ | ------------------------------------ |
| `-h`, `--help`     | Displays help menu                   |
| `-t`, `--tor`      | Starts transparent proxy through Tor |
| `-c`, `--clearnet` | Restores normal internet connection  |
| `-s`, `--status`   | Displays program and service status  |
| `-i`, `--ipinfo`   | Shows current public IP address      |
| `-r`, `--restart`  | Restarts Tor service and changes IP  |
| `-v`, `--version`  | Displays Kalitorify version          |

---
