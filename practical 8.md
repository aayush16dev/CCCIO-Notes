

---

# **Using Host Hunter to Discover and Extract Hostnames from Target IP Addresses**

## Objective

The objective of this practical is to use the **Host Hunter** tool in Kali Linux to discover and extract hostnames associated with target IP addresses and store the results in different output formats for analysis.

## Pre-requisites

1. **Kali Linux System**: A working Kali Linux installation.

2. **Host Hunter Tool**: Must be installed and accessible from the terminal.

3. **Internet / Network Access**: Required for performing reconnaissance.

4. **Terminal Access**: Needed to execute Host Hunter commands.

5. **Basic Networking Knowledge**: Understanding of IP addresses and hostnames.

## Commands as Steps

1. **Start Host Hunter**

   ```bash id="k2t8mr"
   hosthunter
   ```

   **Explanation**: Launches the Host Hunter tool from the terminal.

2. **View Help Options**

   ```bash id="p7w4dx"
   hosthunter -h
   ```

   **Explanation**: Displays all available commands and usage options of Host Hunter.

3. **Extract Hostname from a Target IP**

   ```bash id="v9q3nb"
   hosthunter -t 157.240.16.52
   ```

   **Explanation**: Discovers and extracts the hostname associated with the specified target IP address.

4. **View Saved Results in CSV Format**

   ```bash id="m6u1zy"
   cat vhosts.csv
   ```

   **Explanation**: Displays the scan results automatically saved in the `vhosts.csv` file.

5. **Save Results in TXT Format**

   ```bash id="f4e7hk"
   hosthunter -t 31.13.88.174 -f txt -o details.txt
   ```

   **Explanation**: Saves the extracted hostname information into a custom text file.

6. **Scan Multiple IP Addresses from a File**

   ```bash id="n8r5qc"
   hosthunter ip.list
   ```

   **Explanation**: Performs hostname extraction for all IP addresses listed in the `ip.list` file.

---
