
---

# **Practical: Hosting a Website using Nginx**

## Aim

To install and configure the **Nginx web server** to host a custom HTML webpage and understand basic server block configuration.

---

# Theory

## 1. Web Servers Overview

A **web server** is software that delivers web content such as HTML, CSS, and JavaScript to clients using HTTP or HTTPS protocols.

### Common Web Servers

* **Apache2**

  * Process-based architecture

  * Highly configurable

  * Common in shared hosting
* **Nginx**

  * Event-driven asynchronous architecture

  * High performance with low memory usage

  * Used for reverse proxying and load balancing
* **Caddy**

  * Automatic HTTPS support

  * Simple configuration
* **Tornado**

  * Python-based asynchronous server

  * Suitable for real-time applications
* **Cloudflare**

  * CDN and reverse proxy service

  * Provides caching and DDoS protection
* **WAMP**

  * Windows-based stack

  * Includes Apache, MySQL, and PHP

---

## 2. Nginx Architecture

Nginx uses:

* **Master Process** → manages worker processes

* **Worker Processes** → handle client requests

* **Event-driven Model** → efficiently handles thousands of connections

---

## 3. Reverse Proxy

A **reverse proxy** sits between clients and backend servers.

### Uses

* Load balancing

* SSL termination

* Security enhancement

* Hiding backend servers

---

## 4. Proxy Server Types

| Type          | Function           |
| ------------- | ------------------ |
| Forward Proxy | Client to Internet |
| Reverse Proxy | Internet to Server |

---

## 5. Email Protocols

### SMTP (Simple Mail Transfer Protocol)

* Used for sending emails

* Ports: 25, 587

### IMAP (Internet Message Access Protocol)

* Synchronizes emails across devices

* Ports: 143, 993

### POP3 (Post Office Protocol v3)

* Downloads emails locally

* Ports: 110, 995

---

# Practical Procedure

## 1. Install Nginx

```bash id="m4t8vq"
apt install nginx
```

### Explanation

Installs the Nginx web server package.

---

## 2. Start Nginx Service

```bash id="k7n2py"
service nginx start
```

### Explanation

Starts the Nginx web server service.

---

## 3. Create Website Directory

```bash id="x1u5rd"
cd /var/www

mkdir amit.com
```

### Explanation

Creates a new directory for hosting the custom website.

---

## 4. Create HTML File

```bash id="v9q3mk"
touch index.html && mousepad index.html
```

### Explanation

Creates and opens the `index.html` file for editing.

### Sample Content

```html id="c6w8hn"
<h1>Welcome to Amit Website</h1>
```

---

## 5. Navigate to Nginx Configuration Directory

```bash id="p5d1tx"
cd /etc/nginx
```

### Explanation

Moves to the Nginx configuration directory.

---

## 6. View Available Site Configurations

```bash id="f2m7zk"
ls sites-available
```

### Explanation

Displays available Nginx site configuration files.
The default configuration file will be visible.

---

## 7. Create a New Server Block Configuration

```bash id="r8u4yb"
cp sites-available/default sites-available/amit.com
```

### Explanation

Copies the default Nginx configuration file to create a new configuration for the custom website.

---

## 8. Edit the Server Block Configuration

```bash id="w3n9qe"
mousepad sites-available/amit.com
```

### Modify the Following Lines

* Change line 41 from:

```nginx id="t6x2kc"
html
```

to:

```nginx id="y1v7pm"
amit.com
```

* Change line 46:

```nginx id="d4r8ua"
server_name amit.com
```

* Remove `#` symbols from lines 79–81.

### Explanation

Configures the document root and domain name for the custom website.

---

## 9. Enable the Website

```bash id="n7q5hv"
cd sites-enabled

ln -s ../sites-available/amit.com amit.com

ls -l
```

### Explanation

Creates a symbolic link to enable the new website configuration.

---

## 10. Test Nginx Configuration

```bash id="u2m8rx"
nginx -t
```

### Explanation

Checks the Nginx configuration for syntax errors.

If the test is successful, the configuration is valid.

---

## 11. Fix Configuration Errors (If Test Fails)

```bash id="a9k4wb"
cd ..

mousepad ../sites-enabled/amit.com
```

### Explanation

Opens the enabled configuration file to troubleshoot errors.

Check the placement of `}` around line 90.

Remove the default enabled site:

```bash id="e5v1qn"
unlink /etc/nginx/sites-enabled/default
```

Retry the configuration test:

```bash id="z3t7my"
nginx -t
```

---

## 12. Configure Local DNS Mapping

```bash id="q8n6pc"
mousepad /etc/hosts
```

Add the following entries:

```text id="b4u2kx"
<your ip>   amit.com

0.0.0.0     amit.com
```

### Explanation

Maps the custom domain name to the local system IP address.

---

## 13. Save and Access Website

Save all files and open the browser.

Visit:

```text id="j6r9vd"
http://amit.com
```

### Explanation

Displays the hosted custom website through Nginx.

---

# Observations

* Nginx successfully hosted a custom static webpage.

* Server blocks allow hosting multiple websites on the same server.

* Proper DNS or hosts file mapping is necessary for custom domains.

---

# Conclusion

Nginx is a lightweight and high-performance web server capable of hosting websites efficiently. Through this practical, a custom website was successfully configured using Nginx server blocks and local domain mapping.

---

# Result

A custom website was successfully hosted and accessed using the Nginx web server in Kali Linux.

---
