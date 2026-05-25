
---
# Practical: Hosting index.html Using Portmap with Apache2

## Prerequisites:

- A Linux machine (Ubuntu/Debian-based preferred)
- Apache2 installed
- OpenVPN installed
- Portmap.io account
- A valid `.ovpn` configuration file

---

## Step 1: Install Required Packages

First, install Apache2 if not already installed:

```bash
sudo apt update && sudo apt install apache2 -y
```

Ensure the Apache2 service is running:

```bash
sudo systemctl start apache2
sudo systemctl enable apache2
```

---

## Step 2: Configure Apache2 Web Server

Place your `index.html` file in the web root directory:

```bash
cd /var/www/html
```

Place a HTML file in html folder by the name of index.html

```
<html>
<body>
    <form action="getmethod.php" method="GET">
       UserName:
       <input type="text" name = "UserName"><br>
       City:
       <input type="text" name = "City"><br>
       <input type="submit">
   </form>
</body>
</html>
```

Ensure correct file permissions:

```bash
sudo chmod 644 /var/www/html/index.html
```

Restart Apache to apply changes:

```bash
sudo systemctl restart apache2
```

---

## Step 3: Configure Port Forwarding on Portmap.io

4. Log in to your Portmap.io account.
5. Navigate to **Port Forwarding**.
6. Create a new rule:
    - **Local Port:** `80`
    - **Protocol:** `TCP`
    - **Remote Port:** `46474` (or as assigned by Portmap)
7. Save and apply the rule.

---
## Step 4: Set Up OpenVPN with Portmap

1. Download your `.ovpn` file from Portmap.io (Example: `Ark123.firsAayusht.ovpn`).
2. 
3. Connect to Portmap VPN:
```
openvpn --config Ark123.firsAayusht.ovpn
```
Once connected, you will be assigned a virtual IP address.

---

## Step 5: Access Your Hosted File

After setting up port forwarding, your Apache server should be accessible from the public internet using the Portmap-generated link:

```
http://Ark123-46474.portmap.host:46474
```

Open this link in a web browser, and you should see your `index.html` content displayed.

---