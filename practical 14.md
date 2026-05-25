
---

# Part-2 { **How to Create Your Own Service in Kali Linux**}

---
## **Overview**:  
Converting _Practical 13_ into a service that automatically changes the MAC address every time the system restarts.

## **Steps to Create the Service:**

1. **View an Existing Service File**:
    
    - Display the content of the Apache service unit file:
        
        ```bash
        cat /usr/lib/systemd/system/apache2.service
        ```
        
2. **Create a New Service File**:
    
    - Create and open a new service file named `randmacgen.service`:
        
        ```bash
        mousepad /etc/systemd/system/randmacgen.service
        ```
        
1. **Change to  the Following Configuration**:
    
    ```bash
    [Unit]
    Description=Random mac generator
    After=network-online.target
    Wants=network-online.target
    
    [Service]
    Type=simple
    ExecStart=/bin/bash /home/aayush/Desktop/tools/randmacgen.sh
    
    [Install]
    WantedBy=multi-user.target
    ```
    
2. **Set Proper Permissions**:
    
    - Apply correct permissions to the service file:
        
        ```bash
        chmod 644 /etc/systemd/system/randmacgen.service
        ```
        
        **644 Permissions:**
        
        - Owner: Read & Write
            
        - Group: Read-only
            
        - Others: Read-only
            
3. **Start the Service**:
    
    - Start the service using:
        
        ```bash
        service randmacgen start
        ```
        
4. **Verify MAC Address Change**:
    
    - Check the current and permanent MAC address:
        
        ```bash
        macchanger -s eth0
        ```
        
        This will display the newly generated MAC address and the permanent MAC.

---

#### **Key Points:**

- `/usr/lib/systemd/system/apache2.service` contains service configurations managed by `systemd`.
- `chmod 644` ensures systemd can read the service file securely while preventing unauthorized modification.
- Creating a custom service allows automation of tasks at system startup.
- This service ensures the MAC address changes automatically on every restart.

---
