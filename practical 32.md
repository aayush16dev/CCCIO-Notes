# **Hosting an Onion HTML Page on TOR Network**

---

## **Overview**

This practical demonstrates how to host a hidden HTML website on the **TOR network** using **Tor Hidden Services** and **Nginx**.
The website will be accessible only through the TOR browser using a `.onion` address, ensuring anonymity and privacy.

---

## **Key Components**

* **TOR** – Provides anonymous network routing
* **Nginx** – Web server for hosting HTML content
* **Hidden Service** – Generates `.onion` domain
* **HTML** – Web content

---

## **Step-by-Step Procedure**

---

### **1. Install Required Packages**

```bash
apt install tor
apt install nginx
```

---

### **2. Configure TOR Hidden Service**

Open the TOR configuration file:

```bash
mousepad /etc/tor/torrc
```

Add the following lines at the end:

```bash
HiddenServiceDir /var/lib/tor/hidden_service
HiddenServicePort 80 127.0.0.1:80
```

Save and exit.

Restart TOR:

```bash
service tor restart
```

---

### **3. Obtain Onion Address**

```bash
cat /var/lib/tor/hidden_service/hostname
```

Example output:

```
vpig47jgldcoymwvw4gfopn6cvjli4prpmp6dnskuapd7l2qpdtdsayd.onion
```

Verify hidden service files:

```bash
ls /var/lib/tor/hidden_service
```

Output should show:

```
authorized_clients  hs_ed25519_public_key
hostname            hs_ed25519_secret_key
```

---

### **4. Create Website Files**

```bash
cd /var/www
mkdir ayush
cd ayush
touch index.html
```

Create a basic HTML page inside `index.html`.

Verify structure:

```bash
tree /var/www
```

---

### **5. Configure Nginx**

```bash
cd /etc/nginx
mousepad nginx.conf
```

Remove `#` from the following line (around line 25):

```bash
server_name_in_redirect off;
```

---

### **6. Create New Server Block**

```bash
ls sites-available
cp sites-available/default sites-available/ayush
mousepad sites-available/ayush
```

Edit:

* Remove `default_server` from line 22 & 23
* Change root (around line 41):

```bash
root /var/www/ayush;
```

* Add onion domain (around line 46):

```bash
server_name vpig47jgldcoymwvw4gfopn6cvjli4prpmp6dnskuapd7l2qpdtdsayd.onion;
```

Save file.

---

### **7. Enable New Site**

```bash
cd sites-enabled
ls -alps
ln -s ../sites-available/ayush
ls
```

---

### **8. Final Nginx Fix & Start**

```bash
nginx -t
```

If error occurs, open main config:

```bash
mousepad /etc/nginx/nginx.conf
```

Change:

```bash
server_names_hash_bucket_size 128;
```

Test again:

```bash
nginx -t
service nginx start
```

---

### **9. Access Onion Website**

Open **TOR Browser**
Paste your `.onion` address:

```
vpig47jgldcoymwvw4gfopn6cvjli4prpmp6dnskuapd7l2qpdtdsayd.onion
```

Your HTML page will be displayed.

---
