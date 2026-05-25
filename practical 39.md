# Practical: Using Dmitry for Information Gathering

## Key Points:

- Dmitry (Deep magic Information Gathering Tool) is used for reconnaissance and information gathering.
- It helps in collecting data such as subdomains, email addresses, and open ports.
- Useful for ethical hacking and security analysis.

---

## Prerequisites:

- A Linux-based system (Ubuntu, Kali Linux, or Debian preferred).
- Dmitry installed (available in most package repositories).

### Install Dmitry (if not installed):

```bash
sudo apt update && sudo apt install dmitry -y
```

---

## Procedure to Use Dmitry

### Step 1: Basic Usage

Run the following command to get basic information about a target domain:

```bash
dmitry -iwns example.com
```

### Step 2: Collect Whois Information

```bash
dmitry -w example.com
```

### Step 3: Perform Netcraft Lookup

```bash
dmitry -n example.com
```

### Step 4: Retrieve Subdomains

```bash
dmitry -s example.com
```

### Step 5: Email Address Lookup

```bash
dmitry -e example.com
```

### Step 6: Perform All Scans Together

```bash
dmitry -winse example.com
```

---

## Explanation of Dmitry Options

- `-w`: Perform a WHOIS lookup on the target.
- `-i`: Get the target's IP address.
- `-n`: Perform a Netcraft lookup.
- `-s`: Search for subdomains related to the target.
- `-e`: Look for email addresses related to the target.
- `-p`: Perform a TCP port scan.
- `-b`: Perform a Banners Grab.

---