# How to Change Password of Kali Root User
---

**Overview**:  
Changing the root user's password in Kali Linux is essential for maintaining system security and managing access.

#### Steps to Change the Root Password:

1. **Switch to Superuser Mode**:
    
    - Open the terminal and enter:
        
        ```bash
        sudo su
        ```
        
    - It will prompt for the current Kali Linux password (e.g., `username: kali` and `password: kali` by default).
2. **Change the Root Password**:
    
    - After switching to root mode, type the command:
        
        ```bash
        passwd root
        ```
        
        Replace `root` with any existing username to change the password for a specific user.
3. **Set a New Password**:
    
    - Enter the new password when prompted.
    - Re-type the new password to confirm.
4. **Verify Changes**:
    
    - Log out and re-login using the updated credentials (e.g., `username: root` and the newly set password).

#### Key Points:

- Ensure the new password is strong and secure.
- Default credentials should always be updated to prevent unauthorized access.
- Use `sudo su` cautiously to avoid unintended changes to the system.
- For non-root users, replace `root` with the desired username in the command.