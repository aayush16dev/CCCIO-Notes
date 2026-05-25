----
# **Password Protecting the GRUB Boot Loader in Kali Linux**

## Objective

The objective of this practical is to secure the GRUB boot loader in Kali Linux by setting a password, preventing unauthorized users from modifying boot parameters and gaining privileged system access.

## Pre-requisites

1. **Kali Linux System**: A working Kali Linux installation.
    
2. **Terminal Access**: Required to execute system commands.
    
3. **Root Privileges**: Needed to modify GRUB configuration files.
    
4. **Basic Linux Knowledge**: Familiarity with file editing and system commands.
    

## Commands as Steps

1. **Open the Terminal**
    
    **Action**: Launch the terminal in Kali Linux.
        **Explanation**: The terminal is required to execute GRUB configuration commands.
    
2. **Generate GRUB Password Hash**
    
    `grub-mkpasswd-pbkdf2`
    
    **Explanation**: This command generates a secure GRUB-compatible password hash.  
    Enter a new password when prompted and copy the generated hash.
    
3. **Edit GRUB Configuration File**
    
    `sudo nano /etc/grub.d/00_header`
    
    **Explanation**: Opens the main GRUB header configuration file for editing.
    
4. **Add Superuser and Password Hash**
    
    Add the following lines at the end of the file:
    ```
    `cat <<EOF set superusers="username" password_pbkdf2 username <paste-your-password-hash-here> EOF`
    ```
    
      **Explanation**:  
    Replace `username` with your desired GRUB username and paste the generated hash in place of `<paste-your-password-hash-here>`.  
    This enforces authentication before editing GRUB settings.
    
5. **Save and Exit the File**
    
    **Action**: Press **`Ctrl + O`** to save and **`Ctrl + X`** to exit.
    
    **Explanation**: Saves the configuration changes.
    
6. **Update GRUB Configuration**
    
    ```
    sudo update-grub
    ```
    
    **Explanation**: Applies the new GRUB security settings.
    
7. **Reboot the System**
    
    ```
    sudo reboot
    ```
    
    **Explanation**: Restarts the system to activate the GRUB password protection.
    
8. **Verify Password Protection**
    
    **Action**: When the GRUB screen appears, press **`E`**.  
    Enter the **username and password** when prompted.
    
    **Explanation**: Confirms that GRUB is now protected from unauthorized modification.
    

---](<---

# **Password Protecting the GRUB Boot Loader in Kali Linux**

## Objective

The objective of this practical is to secure the GRUB boot loader in Kali Linux by setting a password, preventing unauthorized users from modifying boot parameters and gaining privileged system access.

---

## Pre-requisites

1. **Kali Linux System**: A working Kali Linux installation.

2. **Terminal Access**: Required to execute system commands.

3. **Root Privileges**: Needed to modify GRUB configuration files.

4. **Basic Linux Knowledge**: Familiarity with file editing and Linux commands.

---

# Commands as Steps

## 1. Open the Terminal

### Action

Launch the terminal in Kali Linux.

### Explanation

The terminal is required to execute GRUB configuration commands and modify system files.

---

## 2. Generate GRUB Password Hash

```bash id="h9qv31"
grub-mkpasswd-pbkdf2
```

### Explanation

This command generates a secure password hash compatible with the GRUB boot loader.

When prompted:

* Enter a new password

* Re-enter the password for confirmation

After successful verification, copy the generated PBKDF2 hash.

---

## 3. Edit GRUB Configuration File

```bash id="m4jk0t"
nano /etc/grub.d/00_header
```

### Explanation

Opens the GRUB header configuration file for editing.

---

## 4. Add Superuser and Password Hash

Add the following lines at the end of the file:

```bash id="0l3rmg"
cat %3C<EOF
set superusers="username"
password_pbkdf2 username <paste-your-password-hash-here%3E
EOF
```

### Explanation

* Replace `username` with the desired GRUB username.

* Replace `<paste-your-password-hash-here>` with the generated password hash.

* These settings enable password authentication for editing GRUB boot entries.

---

## 5. Save and Exit the File

### Action

Press:

* **`Ctrl + O`** to save the file

* **`Ctrl + X`** to exit the editor

### Explanation

This stores the new GRUB security configuration.

---

## 6. Update GRUB Configuration

```bash id="1nkx7v"
update-grub
```

### Explanation

Applies the updated GRUB configuration and regenerates the bootloader settings.

---

## 7. Reboot the System

```bash id="4t4vzg"
reboot
```

### Explanation

Restarts the system to activate GRUB password protection.

---

## 8. Verify Password Protection

### Action

When the GRUB menu appears:

* Press **`E`** to edit boot parameters

* Enter the configured **username and password** when prompted

