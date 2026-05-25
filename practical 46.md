## **Permanent Setup of DVWA on Kali Linux for Penetration Testing**

## Objective
The objective of this practical is to permanently set up the Damn Vulnerable Web Application (DVWA) on Kali Linux for penetration testing. This setup will allow you to practice identifying and exploiting various web application vulnerabilities.

## Pre-requisites
1. **Kali Linux**: Ensure you have Kali Linux installed and running.
2. **Kali Linux Labs**: Ensure the Kali Linux Labs package is installed, which includes DVWA.
3. **Mousepad**: Ensure Mousepad (a text editor) is installed on your system.

## Commands as Steps

1. **Install Kali Linux Labs**
   ```bash
   apt install kali-linux-labs
   ```
   **Explanation**: This command installs the Kali Linux Labs package, which includes DVWA and other useful tools for penetration testing.

2. **Start DVWA**
   ```bash
   dvwa -start
   ```
   **Explanation**: This command starts the DVWA application. It will run DVWA on a local server, typically accessible at `http://localhost:8080/dvwa`.

3. **Access DVWA in Your Browser**
   Open your web browser and navigate to `http://localhost:8080/dvwa` to access the DVWA application.

4. **Reset the Database**
   - **Click on "Reset/Database"**: On the left side of the DVWA interface, click on the "Reset/Database" option to reset the database to its default state.

5. **Copy the Configuration File Path**
   - **Copy the Path**: Copy the path to the DVWA configuration file, which is `/etc/dvwa/config/config.inc.php`.

6. **Open the Configuration File in Mousepad**
   ```bash
   mousepad /etc/dvwa/config/config.inc.php
   ```
   **Explanation**: This command opens the DVWA configuration file in Mousepad, allowing you to make any necessary changes to the configuration.

## Example Usage: Focus on DVWA

### Starting and Interacting with DVWA

1. **Start the DVWA Lab**
   ```bash
   dvwa -start
   ```
   **Explanation**: This command starts the DVWA lab, which is a web application with various vulnerabilities for testing.

2. **Access DVWA in Your Browser**
   Open your web browser and navigate to `http://localhost:8080/dvwa` to access the DVWA application.

3. **Perform Penetration Testing**
   Use tools like Burp Suite, OWASP ZAP, or other penetration testing tools to identify and exploit vulnerabilities in the DVWA application.

### Example: Exploiting SQL Injection in DVWA

1. **Login to DVWA**
   - Navigate to the DVWA login page.
   - Use the default credentials (`admin` for both username and password) to log in.

2. **Set Security Level to Low**
   - After logging in, go to the "Security" tab on the left side.
   - Set the security level to "Low" to make the vulnerabilities easier to exploit.

3. **Navigate to the SQL Injection Vulnerability**
   - Go to the "SQL Injection" tab on the left side.

4. **Exploit the SQL Injection Vulnerability**
   - Enter a payload like `1 OR '1'='1` in the input field and click "Submit".
   - Observe the results to see how the SQL injection payload affects the application.

---