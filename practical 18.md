
---
---

# **Hosting Two Webpages from the Same Server Using Apache2 (Virtual Hosts)**

---

## **Objective**

The objective of this practical is to host **two different websites on a single Apache2 web server** using **Virtual Hosts**. This helps understand how Apache serves different content based on domain names.

---

## **Pre-requisites**

1. **Kali Linux** system with root access

2. **Apache2 Web Server** installed

3. Basic knowledge of Linux directory structure

4. Web browser for testing

---

# **Commands as Steps**

---

## **1. Install Apache2**

```bash id="r8k3vz"
apt install apache2
```

**Explanation**:
Installs the Apache2 web server required to host websites.

---

## **2. Create Website Directories**

```bash id="x2n7qa"
mkdir -p /var/www/aayush.com/public_html

mkdir -p /var/www/amit.com/public_html
```

**Explanation**:
Creates document root folders for both websites.

* `-p` creates parent directories if they do not already exist.

### To Give Ownership

```bash id="m4v9dj"
chown -R $USER:$USER /var/www/aayush.com

chown -R $USER:$USER /var/www/amit.com
```

* `-R` applies ownership changes recursively to all files and folders.

---

## **3. Create Index Files**

```bash id="w7u1pk"
mousepad /var/www/aayush.com/public_html/index.html

mousepad /var/www/amit.com/public_html/index.html
```

### Example Content

```html id="y5t2cm"
<h1>Welcome to Aayush Website</h1>
```

```html id="n8d4lx"
<h1>Welcome to Amit Website</h1>
```

**Explanation**:
Each site gets its own homepage.

---

## **4. Enable and Start Apache2 Service**

```bash id="f1q8re"
systemctl enable apache2

systemctl start apache2
```

**Explanation**:
Ensures Apache starts automatically during boot and runs immediately.

---

## **5. Create Virtual Host Configuration Files**

Copy the default configuration file to create two new virtual hosts:

```bash id="k6z0tw"
cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/aayush.com.conf

cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/amit.com.conf
```

**Explanation**:
Each `.conf` file represents one website configuration.

---

## **6. Edit First Virtual Host Configuration**

```bash id="u3x7gn"
mousepad /etc/apache2/sites-available/aayush.com.conf
```

Modify/add the following:

```apache id="a9m2vb"
ServerAdmin webmaster@aayush.com
DocumentRoot /var/www/aayush.com/public_html
ServerName aayush.com
ServerAlias www.aayush.com
```

**Explanation**:
Defines the domain name and root directory for the first website.

---

## **7. Edit Second Virtual Host Configuration**

```bash id="p2k5eh"
mousepad /etc/apache2/sites-available/amit.com.conf
```

Modify/add the following:

```apache id="z7n4uc"
ServerAdmin webmaster@amit.com
DocumentRoot /var/www/amit.com/public_html
ServerName amit.com
ServerAlias www.amit.com
```

**Explanation**:
Defines the second website with a different domain name and document root.

---

## **8. Enable Virtual Hosts**

```bash id="h5w1qy"
a2ensite aayush.com.conf

a2ensite amit.com.conf

a2dissite 000-default.conf
```

**Explanation**:
Activates both virtual host configurations and disables the default Apache site.

---

## **9. Assign Domains to Local IP**

```bash id="v8r6tb"
mousepad /etc/hosts
```

Add:

```text id="q4j2nm"
<User_ip> aayush.com

<User_ip> amit.com
```

**Explanation**:
Maps both domain names to the local system IP address for testing purposes.

---

## **10. Restart Apache2**

```bash id="d1c9zk"
systemctl restart apache2
```

**Explanation**:
Applies all Apache configuration changes.

---

## **11. Test in Browser**

Open the web browser and visit:

```text id="t7m3yv"
http://aayush.com

http://amit.com
```

Each domain should display its respective webpage.

---

# **Result**

Two different websites were successfully hosted on a single Apache2 server using Virtual Hosts.

---

