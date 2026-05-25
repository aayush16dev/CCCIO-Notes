
---

# **Configuring and Using an SSH Server in Kali Linux**

## Objective

The objective of this practical is to configure and start the SSH server on Kali Linux and establish a secure remote connection from a Windows system using PuTTY or the built-in SSH command.

## Pre-requisites

1. **Kali Linux System**: A working Kali Linux installation.
    
2. **Windows System**: For remote connection testing.
    
3. **Internet Connection**: To install required packages.
    
4. **Terminal Access**: Needed to execute SSH commands.
    
5. **Network Connection**: Both systems must be on the same network or in Bridge Mode.
    

## Commands as Steps

1. **Check SSH Server Installation**
    
    ```bash
    apt list openssh-server
    ```
    
    **Explanation**: Checks whether the OpenSSH server package is available on the system.
    
2. **Update OpenSSH Server**
    
    ```bash
    apt upgrade openssh-server
    ```
    
    **Explanation**: Ensures the latest version of the SSH server is installed.
    
3. **Check IP Address**
    
    ```bash
    ifconfig
    ```
    
    **Explanation**: Displays the IP address of the Kali Linux system.
    
4. **Start SSH Service**
    
    ```bash
    service ssh start
    ```
    
    **Explanation**: Starts the SSH server service.
    
5. **Verify SSH Service Status**
    
    ```bash
    service ssh status
    ```
    
    **Explanation**: Confirms that the SSH service is running correctly.
    
6. **Configure Network Connection**
    
    **Action**:  
    Ensure both Kali Linux and Windows systems are on the same network or configured in **Bridge Mode**.  
    Example:
    
    - Kali IP: `192.168.128.128`
        
    - Windows IP: `192.168.128.130`
        
    
    **Explanation**: Network connectivity is required for remote access.
    
7. **Install SSH Client on Windows**
    
    **Action**:  
    Download and install **PuTTY** from the official website.
    
    **Explanation**: PuTTY is used as the SSH client for connecting to Kali Linux.
    
8. **Connect Using PuTTY**
    
    **Action**:  
    In PuTTY, enter:
    
    - **Host/IP**: Kali Linux IP address
        
    - **Port**: `22`
        
    - Login using your Kali **username** and **password**
        
    
    **Explanation**: Establishes a secure remote SSH connection.
    
9. **Verify Connection**
    
    **Action**:  
    After login, the Kali Linux terminal appears on the Windows system.
    
    **Explanation**: Confirms successful SSH communication.
    

---

## **Alternative Method: SSH via Windows Command Prompt**

10. **Connect Using Windows Command Prompt**
    
    ```bash
    ssh <username>@<Kali-IP>
    ```
    
    **Example**:
    
    ```bash
    ssh root@192.168.128.128
    ```
    
    **Explanation**: Uses Windows' built-in SSH client to connect directly.
    
11. **Provide Password**
    
    **Action**: Enter the user password when prompted.
    
    **Explanation**: Authenticates the SSH session.
    
12. **Test Remote Operations**
    
    **Action**: Create a folder from the Windows terminal and verify it appears on Kali Linux.
    
    **Explanation**: Confirms real-time remote control of the Kali system.
    

---](<---

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

--->)