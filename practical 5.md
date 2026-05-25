
---

# **FTP File Sharing and Configuration in Kali Linux**

## Objective

The objective of this practical is to configure an FTP server on Kali Linux using **vsftpd**, create and manage FTP users, and establish a successful file transfer connection between Kali Linux and a client system.

## Pre-requisites

1. **Kali Linux System**: A working Kali Linux installation.

2. **Internet Connection**: Required to install vsftpd.

3. **Terminal Access**: Needed to execute system commands.

4. **Client System**: A Windows machine with **FileZilla** installed.

5. **Network Connection**: Both systems must be on the same network or in Bridge Mode.

## Commands as Steps

1. **Install FTP Server**

   ```bash id="v7m3pk"
   apt install vsftpd
   ```

   **Explanation**: Installs the **vsftpd** FTP server package.

2. **Navigate to Configuration Directory**

   ```bash id="0k2n6x"
   cd /etc
   ```

   **Explanation**: Moves to the directory containing FTP configuration files.

3. **Grant Permissions to Configuration File**

   ```bash id="w8pz5q"
   chmod +777 vsftpd.conf
   ```

   **Explanation**: Grants permission to edit the configuration file.

4. **Edit FTP Configuration**

   ```bash id="g5d2tr"
   mousepad vsftpd.conf
   ```

   Modify the following lines:

   ```bash id="u4v1hn"
   local_enable=YES
   chroot_local_user=YES
   chroot_local_user=YES
   chroot_list_enable=YES
   chroot_list_file=/etc/vsftpd.chroot_list
   ```

   **Explanation**: These settings enable local users and restrict them to their home directories.

5. **Create chroot List File**

   ```bash id="r9y0cb"
   touch vsftpd.chroot_list
   ```

   **Explanation**: Creates a file that will store the usernames allowed for FTP access.

6. **Create a New FTP User**

   ```bash id="n2k8la"
   adduser massmatic
   ```

   **Explanation**: Creates a new FTP user and sets its password.

7. **Verify User Creation**

   ```bash id="f3x7je"
   cat /etc/passwd
   ```

   **Explanation**: Displays the list of system users to confirm the new user exists.

8. **Grant Permissions to chroot List**

   ```bash id="m1t4vo"
   chmod +777 vsftpd.chroot_list
   ```

   **Explanation**: Allows editing the chroot user list file.

9. **Add User to chroot List**

   ```bash id="c8w6yb"
   mousepad vsftpd.chroot_list
   ```

   Add the username:

   ```bash id="z0p4rn"
   massmatic
   ```

   **Explanation**: Authorizes the user for FTP access.

10. **Start FTP Service**

    ```bash id="q7d9uk"
    service vsftpd start
    ```

    **Explanation**: Starts the FTP server service.

11. **Check IP Address**

    ```bash id="a6n3et"
    ifconfig
    ```

    **Explanation**: Retrieves the Kali Linux system’s IP address.

12. **Configure Client System**

    **Action**:

    * Ensure both machines are on the same network or in Bridge Mode.

    * Install **FileZilla** on the Windows system.

    **Explanation**: Prepares the client machine for FTP connection.

13. **Test FTP Connection**

    **Action**:
    In FileZilla, enter:

    * **Host**: Kali Linux IP address

    * **Username**: `massmatic`

    * **Password**: User’s password

    **Explanation**: Confirms successful FTP connection and file transfer between systems.

---
