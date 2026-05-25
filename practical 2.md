
---



# **Resetting or Recovering a Forgotten Login Password in Kali Linux**

## Objective

The objective of this practical is to learn how to reset or recover a forgotten login password in Kali Linux by modifying boot parameters and accessing the system through the Bash command-line interface.

---

## Pre-requisites

1. **Kali Linux System**: A machine with Kali Linux installed.

2. **Physical Access**: Required to modify bootloader settings during startup.

3. **Basic Linux Knowledge**: Familiarity with Linux commands and system files.

---

# Commands as Steps

## 1. Restart the System

### Action

Restart the Kali Linux system.

### Explanation

Restarting the system is necessary to access the bootloader configuration menu.

---

## 2. Access the Bootloader Menu

### Action

When the GRUB bootloader screen appears, press **`E`** to edit the boot parameters.

### Explanation

This opens the boot configuration in edit mode before the operating system starts.

---

## 3. Modify Boot Parameters

### Action

Locate the line containing:

```bash id="d6w23q"
ro
```

Replace it with:

```bash id="3sfp4u"
rw
```

Then append the following at the end of the same line:

```bash id="wzz30o"
init=/bin/bash
```

### Explanation

* `rw` enables read and write access to the root filesystem.

* `init=/bin/bash` starts the system directly into a Bash shell with administrative privileges.

---

## 4. Save and Boot with New Settings

### Action

Press **`Ctrl + X`** to boot the system using the modified configuration.

### Explanation

This loads Kali Linux with the updated boot parameters and opens a root shell.

---

## 5. Access Bash Command Line

### Action

The system will boot directly into the Bash command-line interface.

### Explanation

This provides direct root-level access without requiring login authentication.

---

## 6. List All Users

```bash id="hupv8j"
cat /etc/passwd
```

### Explanation

Displays all user accounts available on the system.

---

## 7. Reset the Password

```bash id="kq4kvn"
passwd <username>
```

### Example

```bash id="79u4rk"
passwd root
```

### Explanation

This command creates a new password for the selected user account.

---

## 8. Restart the System

```bash id="n4qmkh"
exit
```

### Explanation

Exits the Bash shell and allows the system to continue the normal boot process.

---

## 9. Login Using the New Password

### Action

Log in using the newly created password.

