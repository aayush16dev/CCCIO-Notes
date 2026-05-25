
---
# **Performing MAC Address Spoofing Using Nmap in Kali Linux**

## Objective

The objective of this practical is to understand and perform **MAC address spoofing** using the Nmap tool in Kali Linux in order to enhance anonymity and test network security scenarios.

## Pre-requisites

1. **Kali Linux System**: A working Kali Linux installation.

2. **Nmap Tool**: Must be installed on the system.

3. **Internet / Network Access**: Required for scanning and testing.

4. **Terminal Access**: Needed to execute commands.

5. **Basic Networking Knowledge**: Understanding of MAC addresses and network scanning.

## Commands as Steps

1. **MAC Spoofing by Vendor**

   ```bash id="x4t7nk"
   nmap massmatic.biz -v -p 1-65535 --spoof-mac dell
   ```

   **Explanation**:
   Spoofs the MAC address based on the vendor name (**Dell** in this case) while performing a full port scan.

   * `-v`: Enables verbose output

   * `-p 1-65535`: Scans all ports

   * `--spoof-mac dell`: Generates a MAC address associated with Dell

2. **Random MAC Address Spoofing**

   ```bash id="m9u2dr"
   nmap massmatic.biz -v -p 1-65535 --spoof-mac 0
   ```

   **Explanation**:
   Generates and uses a completely random MAC address during the scan.

3. **Manual MAC Address Spoofing**

   ```bash id="k6q8ye"
   nmap massmatic.biz -v -p 1-65535 --spoof-mac 00:93:11:15:97:07
   ```

   **Explanation**:
   Uses a custom user-defined MAC address for the scan.

---
