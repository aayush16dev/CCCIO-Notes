
---

# Practical Guide for Hosting Your Own Web Server Using Apache2, PHP, and Portmap.io

A web server is a system that stores, processes, and delivers web pages to users over a network. By hosting your own web server, you can serve HTML pages, run PHP scripts, and make your website accessible over the internet. This practical demonstrates how to set up a local Apache web server with PHP support and expose it publicly using Apache HTTP Server, PHP, and Portmap.io.

## Objective:
To host a local web server using Apache2 and PHP, and make it publicly accessible over the internet using Portmap.io.

## Prerequisites:
* A Linux system (Ubuntu/Debian/Kali Linux preferred)
* Internet connectivity
* Basic knowledge of Linux commands
* A Portmap.io account
* OpenVPN installed
* A valid `.ovpn` configuration file from Portmap.io

---

## Step 1: Install Required Packages
Install Apache web server and PHP support:

**Bash**

```bash
sudo apt update
sudo apt install apache2 php libapache2-mod-php -y
```

**Explanation:**
This installs:

* **Apache2** → Web server software
* **PHP** → Server-side scripting language
* **libapache2-mod-php** → Enables Apache to execute PHP files

---

## Step 2: Start and Enable Apache Service
**Bash**

```bash
sudo systemctl start apache2
sudo systemctl enable apache2
```

**Explanation:**
Starts the Apache service and ensures it automatically starts after reboot.

---

## Step 3: Configure the Web Root Directory
Navigate to Apache's default web directory:

**Bash**

```bash
cd /var/www/html
```

**Explanation:**
This is the default directory from which Apache serves web content.

---

## Step 4: Create the HTML Web Page
Create an `index.html` file inside `/var/www/html`.

**Bash**

```bash
sudo nano /var/www/html/index.html
```

Paste the following HTML code:

```html
<html>
<body>
    <form action="getmethod.php" method="GET">
       UserName:
       <input type="text" name="UserName"><br>

       City:
       <input type="text" name="City"><br>

       <input type="submit">
    </form>
</body>
</html>
```

**Explanation:**
This HTML page creates a simple form that accepts user input.

---

## Step 5: Create a PHP Information File
Create a PHP file:
**Bash**

```bash
sudo nano /var/www/html/info.php
```

Paste the following code:

```php
<?php
phpinfo();
?>
```

**Explanation:**
This file displays PHP configuration details and confirms PHP is working properly.

---

## Step 6: Set File Permissions
**Bash**

```bash
sudo chmod 644 /var/www/html/index.html
sudo chmod 644 /var/www/html/info.php
```

**Explanation:**
Provides appropriate read permissions for Apache.

---

## Step 7: Restart Apache
**Bash**

```bash
sudo systemctl restart apache2
```

**Explanation:**
Reloads Apache with the new configuration and files.

---

## Step 8: Verify Local Hosting
Open your browser and visit:

```text
http://localhost
```

To verify PHP support:
```text
http://localhost/info.php
```

**Explanation:**
If configured correctly:
* `localhost` displays your HTML form.
* `localhost/info.php` displays PHP configuration details.

---

# Portmap.io Integration

Since Portmap.io was configured in the previous practical, we now integrate that setup to make the local Apache server publicly accessible.

---

## Step 9: Connect to Portmap VPN

Use your previously downloaded `.ovpn` file.
**Bash**

```bash
openvpn --config Ark123.firsAayusht.ovpn
```

**Explanation:**
This establishes a secure VPN tunnel with Portmap.io.

---
## Step 10: Configure Port Forwarding

Log in to your Portmap.io dashboard and configure:

| Setting     | Value               |
| ----------- | ------------------- |
| Local Port  | `80`                |
| Protocol    | `TCP`               |
| Remote Port | Assigned by Portmap |

Example:
```text
46474
```

**Explanation:**
Incoming traffic on the public Portmap address will be forwarded to your local Apache server.

---

## Step 11: Access Your Hosted Web Server Publicly

After Portmap is connected, your website becomes accessible via the Portmap-generated URL.
Example:

```text
http://Ark123-46474.portmap.host:46474
```

**Explanation:**
Anyone with this URL can access your hosted website over the internet.

---

## Testing the Hosted Content
### HTML Page

Opening the Portmap URL displays:

* Username field
* City field
* Submit button

### PHP Page
Append `/info.php` to the URL:

```text
http://Ark123-46474.portmap.host:46474/info.php
```

This displays PHP server configuration details.

---

## Example Scenario:
Suppose you host a registration form on your Linux machine.

1. Apache serves the HTML form locally.
2. Portmap forwards internet traffic to your system.
3. Remote users can fill out the form using your public Portmap URL.

This demonstrates real-world remote web hosting.

---

## Explanation of Functionality:
This practical combines multiple technologies:

### Apache HTTP Server
Hosts and serves web pages.
### PHP
Processes dynamic web content.
### Portmap.io
Exposes your local server to the public internet.
### OpenVPN

Creates a secure tunnel between your machine and Portmap.

---
## Applications:

* Hosting personal websites
* Testing web applications
* Remote form collection
* PHP development and debugging
* Security research and penetration testing

---
