
---

# **Using WHOAMI Tool to Avoid Anonymity Leaks on Kali Linux**

## Objective

The objective of this practical is to understand how to use the **WHOAMI** tool on Kali Linux to prevent anonymity leaks and enhance system privacy by checking and securing system configurations.

## Pre-requisites

1. **Kali Linux**: A running Kali Linux system.
    
2. **Git**: Installed to clone the WHOAMI project repository.
    
3. **Internet Connection**: Required to download the tool from GitHub.
    
4. **Terminal Access**: To execute all commands.
    

## Commands as Steps

1. **Clone the WHOAMI Tool Repository**
    
    ```bash
    git clone https://github.com/owerdogan/whoami-project.git
    ```
    
    **Explanation**: This command downloads the WHOAMI project from GitHub to your local system or virtual machine.
    
2. **List Directory Contents**
    
    ```bash
    ls
    ```
    
    **Explanation**: Displays the list of files and folders to confirm the repository has been cloned successfully.
    
3. **Navigate to the Project Directory**
    
    ```bash
    cd whoami-project
    ```
    
    **Explanation**: Moves into the WHOAMI project directory.
    
4. **Verify Project Files**
    
    ```bash
    ls
    ```
    
    **Explanation**: Shows the files inside the project directory.
    
5. **Install the WHOAMI Tool**
    
    ```bash
    make install
    ```
    
    **Explanation**: Installs the WHOAMI tool on the system.
    
6. **Check System Date**
    
    ```bash
    date
    ```
    
    **Explanation**: Displays the current system date and time.
    
7. **Check Hostname**
    
    ```bash
    cat /etc/hostname
    ```
    
    **Explanation**: Displays the system’s hostname.
    
8. **Check Network Interface MAC Address**
    
    ```bash
    ifconfig eth0 | grep ether
    ```
    
    **Explanation**: Displays the MAC address of the network interface, which is important for tracking anonymity leaks.
    
9. **Start WHOAMI Tool**
    
    ```bash
    kali-whoami --start
    ```
    
    **Explanation**: Launches the WHOAMI tool to begin protecting the system against anonymity leaks.
    
10. **Activate All WHOAMI Features**
    

**Action**: Press all numbers from **1 to 9**, one by one, and then press **Enter** to activate all security features.

**Explanation**: This enables all available anonymity and privacy protection mechanisms of the WHOAMI tool.

11. **Re-check System Information**
    

```bash
date
cat /etc/hostname
ifconfig eth0 | grep ether
```

**Explanation**: These commands are executed again to verify that system information has been modified or protected after activating WHOAMI.

## Additional Notes

- **Purpose**: WHOAMI helps in preventing information leaks that may reveal the identity of the user.
    
- **Ethical Use**: This tool should be used only for learning and legitimate privacy protection purposes.
    
- **Observation**: After activation, system identifiers such as hostname and MAC address may appear modified, enhancing anonymity.
    

By completing this practical, the objective of understanding and applying anonymity protection techniques using the WHOAMI tool is successfully achieved.

---](<---

# **Using WHOAMI Tool to Avoid Anonymity Leaks on Kali Linux**

## Objective

The objective of this practical is to understand how to use the **WHOAMI** tool on Kali Linux to prevent anonymity leaks and enhance system privacy by checking and securing system configurations.

---

## Pre-requisites

1. **Kali Linux**: A running Kali Linux system.

2. **Git**: Installed to clone the WHOAMI project repository.

3. **Internet Connection**: Required to download the tool from GitHub.

4. **Terminal Access**: To execute all commands.

---

# Commands as Steps

## 1. Clone the WHOAMI Tool Repository

```bash
git clone https://github.com/owerdogan/whoami-project.git
```

### Explanation

This command downloads the WHOAMI project repository from GitHub to the Kali Linux system.

---

## 2. List Directory Contents

```bash
ls
```

### Explanation

Displays the files and folders in the current directory to confirm that the repository has been cloned successfully.

---

## 3. Navigate to the Project Directory

```bash
cd whoami-project
```

### Explanation

Moves into the WHOAMI project directory.

---

## 4. Verify Project Files

```bash
ls
```

### Explanation

Displays the files and folders available inside the WHOAMI project directory.

---

## 5. Install the WHOAMI Tool

```bash
make install
```

### Explanation

Installs the WHOAMI tool and its required components into the Kali Linux system.

---

## 6. Check System Date

```bash
date
```

### Explanation

Displays the current system date and time before enabling anonymity protection.

---

## 7. Check Hostname

```bash
cat /etc/hostname
```

### Explanation

Displays the current hostname of the system.

---

## 8. Check Network Interface MAC Address

```bash
ifconfig eth0 | grep ether
```

### Explanation

Displays the MAC address of the `eth0` network interface, which can be used for device identification and tracking.

---

## 9. Start WHOAMI Tool

```bash
kali-whoami --start
```

### Explanation

Starts the WHOAMI tool and launches its anonymity protection interface.

---

## 10. Activate All WHOAMI Features

### Action

Press all numbers from **1 to 9** one by one, then press **Enter** to activate all available security and anonymity protection features.

### Explanation

This enables all privacy protection mechanisms provided by the WHOAMI tool, including hostname masking, MAC address randomization, and system hardening options.

---

## 11. Re-check System Information

```bash
date

cat /etc/hostname

ifconfig eth0 | grep ether
```

### Explanation

These commands are executed again to verify whether the system information has been modified or protected after enabling WHOAMI protections.

---

