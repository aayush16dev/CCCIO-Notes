
## **Setting Up and Using PentestLab on Kali Linux for Penetration Testing**

### Objective
The objective of this practical is to set up and use PentestLab on Kali Linux to deploy and manage various penetration testing labs, including Bee-Logged (bwapp) and Damn Vulnerable Web Application (DVWA).

### Pre-requisites
1. **Kali Linux**: Ensure you have Kali Linux installed and running.
2. **Git**: Ensure Git is installed on your system to clone the PentestLab repository.
3. **Docker**: Ensure Docker is installed, as PentestLab uses Docker to deploy labs.
4. **Kali Linux Labs**: Ensure the Kali Linux Labs package is installed for additional tools and configurations.

### Commands as Steps

1. **Clone the PentestLab Repository**
   ```bash
   git clone https://github.com/eystsen/pentestlab
   ```
   **Explanation**: This command clones the PentestLab repository from GitHub to your local machine.

2. **Navigate to the PentestLab Directory**
   ```bash
   cd pentestlab
   ```
   **Explanation**: This command changes the current directory to the PentestLab directory.

3. **Install Docker**
   ```bash
   apt install docker.io
   ```
   **Explanation**: This command installs Docker, which is required for PentestLab to deploy and manage labs.

4. **Make the PentestLab Script Executable**
   ```bash
   chmod +x pentestlab.rb
   ```
   **Explanation**: This command makes the `pentestlab.sh` script executable, allowing you to run it.

5. **Run the PentestLab Script**
   ```bash
   ./pentestlab.rb
   ```
   **Explanation**: This command runs the PentestLab script, which provides a menu of available labs and options.

6. **Start the Bee-Logged (bwapp) Lab**
   ```bash
   ./pentestlab.rb start bwapp
   ```
   **Explanation**: This command starts the Bee-Logged (bwapp) lab, which is a web application with various vulnerabilities for testing.

7. **Stop the Bee-Logged (bwapp) Lab**
   ```bash
   ./pentestlab.rb stop bwapp
   ```
   **Explanation**: This command stops the Bee-Logged (bwapp) lab.

8. **Start the Damn Vulnerable Web Application (DVWA) Lab**
   ```bash
   ./pentestlab.rb start dvwa
   ```
   **Explanation**: This command starts the Damn Vulnerable Web Application (DVWA) lab, which is another web application with various vulnerabilities for testing.

9. **Stop the Damn Vulnerable Web Application (DVWA) Lab**
   ```bash
   ./pentestlab.rb stop dvwa
   ```
   **Explanation**: This command stops the Damn Vulnerable Web Application (DVWA) lab.

10. **Install Kali Linux Labs**
    ```bash
    apt install kali-linux-labs
    ```
    **Explanation**: This command installs the Kali Linux Labs package, which provides additional tools and configurations for penetration testing.

11. **Start DVWA Using Kali Linux Labs**
    ```bash
    dvwa-start
    ```
    **Explanation**: This command starts the DVWA lab using the Kali Linux Labs package.

12. **Edit the DVWA Configuration File**
    ```bash
    nano etc/dvwa/config/config.inc.php
    ```
    **Explanation**: This command opens the DVWA configuration file in the nano text editor, allowing you to make any necessary changes to the configuration.

### Example Usage: Focus on bwapp and dvwa

#### Starting and Interacting with bwapp

1. **Start the bwapp Lab**
   ```bash
   ./pentestlab.sh start bwapp
   ```
   **Explanation**: This command starts the bwapp lab, which is a web application with various vulnerabilities for testing.

2. **Access bwapp in Your Browser**
   Open your web browser and navigate to `http://localhost:8080/bwapp` to access the bwapp application.

3. **Perform Penetration Testing**
   Use tools like Burp Suite, OWASP ZAP, or other penetration testing tools to identify and exploit vulnerabilities in the bwapp application.

#### Starting and Interacting with DVWA

1. **Start the DVWA Lab**
   ```bash
   ./pentestlab.sh start dvwa
   ```
   **Explanation**: This command starts the DVWA lab, which is another web application with various vulnerabilities for testing.

2. **Access DVWA in Your Browser**
   Open your web browser and navigate to `http://localhost:8080/dvwa` to access the DVWA application.

3. **Perform Penetration Testing**
   Use tools like Burp Suite, OWASP ZAP, or other penetration testing tools to identify and exploit vulnerabilities in the DVWA application.

### Additional Notes
- **Documentation**: Refer to the PentestLab documentation for detailed information on each lab and its configuration options. The documentation is usually available in the repository's README file or on the GitHub page.
- **Customization**: You can customize the labs by modifying the configuration files and scripts provided by PentestLab.
- **Ethical Considerations**: Ensure you have explicit permission to test the target systems. Unauthorized testing is illegal and unethical.

By following these steps, you should be able to set up and use PentestLab on Kali Linux to deploy and manage various penetration testing labs, including Bee-Logged (bwapp) and Damn Vulnerable Web Application (DVWA). This practical will help you understand how to leverage these labs for different types of penetration testing activities.