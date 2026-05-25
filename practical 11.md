### How to Change Kali Linux Hostname Using Terminal
---

##### **Overview**:  
Changing the hostname in Kali Linux helps personalize the system or align it with specific network configurations.

#### Steps to Change the Hostname:

1. **Check the Current Hostname**:
    
    - Open the terminal and type:
        
        ```bash
        hostname
        ```
        
2. **Temporarily Change the Hostname**:
    
    - Use the following command to set a temporary hostname:
        
        ```bash
        hostname new_hostname
        ```
        
        Replace `new_hostname` with your desired hostname.
3. **View the Hostname Configuration File**:
    
    - To check the current hostname saved in the configuration file:
        
        ```bash
        cat /etc/hostname
        ```
        
4. **Permanently Change the Hostname**:
    
    - Use the `hostnamectl` command to set a permanent hostname:
        
        ```bash
        hostnamectl set-hostname new_hostname
        ```
        
5. **Verify the Changes**:
    
    - Confirm the updated hostname by typing:
        
        ```bash
        hostnamectl
        ```
        
6. **Restart the System** (Optional):
    
    - Restart the system for changes to fully apply, if necessary:
        
        ```bash
        sudo reboot
        ```
        

#### Key Points:

- Temporary hostname changes last only until the system is restarted.
- For permanent changes, always update the `/etc/hostname` file using `hostnamectl`.