
---

# ** Random MAC Address Generator and How to Create Your Own Service in Kali Linux ** 

---

**Overview**:  
Using the `macchanger` tool to generate and apply a random MAC address for network interface security and anonymity.

#### **Steps to Generate a Random MAC Address:**

1. **Check Current MAC Address**:
    
    - Use the following command to view the current and permanent MAC address:
        
        ```bash
        macchanger -s eth0
        ```
        
2. **Generate a Random MAC Address Automatically**:
    
    - Apply a completely random MAC address using:
        
        ```bash
        macchanger -r eth0
        ```
        
3. **Create a Vendor List File**:
    
    - Store all vendor OUIs in a text file:
        
        ```bash
        macchanger -l > vendormac.txt
        ```
        
4. **Count Available Vendor MACs**:
    
    - Check how many vendor entries are stored:
        
        ```bash
        wc -l vendormac.txt
        ```
        
5. **Select a Random Vendor MAC**:
    
    - Display a random vendor entry:
        
        ```bash
        shuf -n 1 vendormac.txt
        ```
        
6. **Extract Only the Vendor MAC**:
    
    - Use `awk` to display only the vendor OUI:
        
        ```bash
        shuf -n 1 vendormac.txt | awk '{print $3}'
        ```
        
7. **Generate Random Hexadecimal Values**:
    
    - Convert decimal to hexadecimal:
        
        ```bash
        printf '%02x' 123
        ```
        
        Output example:
        
        ```
        7b
        ```
        
        _Note: Output is always in hexadecimal._
        
8. **Generate MAC Structure Format**:
    
    - Create a MAC structure:
        
        ```bash
        printf '%02x:%02x:%02x' 465 47 12
        ```
        
        Output example:
        
        ```
        1d:2f:0c
        ```
        
9. **Generate Random Last 3 Bytes**:
    
    - Generate random values between 0–255:
        
        ```bash
        printf '%02x:%02x:%02x' $[RANDOM%256] $[RANDOM%256] $[RANDOM%256]
        ```
        
10. **Automate Using Shell Script**:
    
    - Create and edit a script file:
        
        ```bash
        touch randmacgen.sh
        mousepad randmacgen.sh
        ```
        
11. **Script Option A** _(May cause issues in Kali 2023+)_:
    
    ```bash
    #!/bin/bash
    macchanger -l > vendormac.txt
    ouimac=$(shuf -n 1 vendormac.txt | awk '{print $3}')
    uaamac=$(printf '%02x:%02x:%02x' $[RANDOM%256] $[RANDOM%256] $[RANDOM%256])
    macchanger -m "$ouimac:$uaamac" eth0
    ```
    
12. **Script Option B (Recommended)**:
    
    ```bash
    #!/bin/bash
    
    new_mac=$(macchanger -l | shuf -n 1 | awk '{print $3}')
    aui_mac=$(printf '%02x:%02x:%02x' $(($RANDOM % 256)) $(($RANDOM % 256)) $(($RANDOM % 256)))
    
    macchanger -m "$new_mac:$aui_mac" eth0
    ```
    

---

#### **Key Points:**

- `macchanger` allows MAC spoofing for privacy and security.
    
- `awk` is used for efficient text extraction.
    
- Randomization helps avoid device tracking.
    
- Scripts automate MAC address generation.
    

---
