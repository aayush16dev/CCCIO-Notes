
---
# Practical Guide for Password Protecting a Folder in Apache HTTP Server

Password protection in Apache2 allows administrators to restrict access to specific directories using username and password authentication. This practical demonstrates how to create a protected folder inside an Apache web server using `.htaccess` and `.htpasswd` authentication.

---

# Objective

To configure password-based authentication for a directory hosted on Apache2 using `.htaccess` and `.htpasswd`.

---

# Prerequisites

* Kali Linux or any Debian-based Linux distribution
* Apache2 installed
* Basic understanding of Linux commands
* Root or sudo privileges

---

# Introduction

Apache HTTP Server supports Basic Authentication using:

* `.htpasswd` → stores usernames and encrypted passwords
* `.htaccess` → applies authentication rules to directories

This mechanism is commonly used to protect:

* Admin panels
* Private documents
* Internal web resources
* Development folders

---

# Step 1: Navigate to Web Directory

Open the terminal and move to the web root directory:

**Bash**

```bash id="y8jz3d"
cd /var/www
```

---

# Step 2: Create Website Directory

Create a new website folder:

**Bash**

```bash id="jlwmx5"
mkdir aayush.com
```

---

# Step 3: Create an HTML Page

Create a simple HTML file:

**Bash**

```bash id="m0mjlf"
mousepad /var/www/aayush.com/index.html
```

Example HTML code:

```html id="jlwmv8"
<html>
<head>
<title>Apache Authentication Demo</title>
</head>

<body>
<h1>Welcome to Aayush.com</h1>
</body>
</html>
```

**Explanation:**
This page acts as the main website homepage.

---

# Step 4: Create a Protected Folder

Create a folder named `DOCS`:

**Bash**

```bash id="0v0hhn"
mkdir /var/www/aayush.com/DOCS
```

---

# Step 5: Create a File Inside DOCS

Move into the folder:

**Bash**

```bash id="bdjlwm"
cd /var/www/aayush.com/DOCS
```

Create a text file:

**Bash**

```bash id="h3zhc9"
touch abc.txt
```

Open and edit the file:

**Bash**

```bash id="4sglhm"
mousepad abc.txt
```

Add some sample data inside the file.

---

# Step 6: Start Apache2 Service

**Bash**

```bash id="tjlwmf"
service apache2 start
```

---

# Step 7: Verify Website

Open the browser and visit:

```text id="jlwm6s"
http://localhost
```

You should see:

* `index.html`
* `DOCS` folder

At this stage, the folder is publicly accessible.

---

# Step 8: Create Username and Password File

Run the following command:

**Bash**

```bash id="jlwm4r"
htpasswd -c /etc/apache2/.htpasswd aayush
```

The terminal prompts:

```text id="1djlwm"
New password:
Re-type new password:
```

**Explanation:**
Creates a hidden password file containing encrypted credentials.

---

# Step 9: View Password Hash

**Bash**

```bash id="jlwm3f"
cat /etc/apache2/.htpasswd
```

Example output:

```text id="jlwm21"
aayush:$apr1$zM9x...encryptedhash...
```

**Explanation:**
Passwords are stored as encrypted hashes instead of plaintext.

---

# Step 10: Create Apache Configuration File

Copy the default Apache configuration:

**Bash**

```bash id="jlwmpp"
cp /etc/apache2/sites-enabled/000-default.conf /etc/apache2/sites-enabled/aayush.com.conf
```

---

# Step 11: Edit Apache Configuration

Open the configuration file:

**Bash**

```bash id="jlwm87"
mousepad /etc/apache2/sites-enabled/aayush.com.conf
```

Add the following configuration near the Directory settings:

```apache id="jlwm98"
<Directory "/var/www/aayush.com/DOCS">
    AuthType Basic
    AuthName "This is area 51"
    AuthUserFile /etc/apache2/.htpasswd
    Require valid-user
</Directory>
```

---

# Explanation of Configuration

| Directive            | Purpose                          |
| -------------------- | -------------------------------- |
| `AuthType Basic`     | Enables basic authentication     |
| `AuthName`           | Message displayed in login popup |
| `AuthUserFile`       | Path to password file            |
| `Require valid-user` | Allows authenticated users only  |

---

# Step 12: Create .htaccess File

Open:

**Bash**

```bash id="jlwm7w"
mousepad /var/www/aayush.com/DOCS/.htaccess
```

Add the following:

```apache id="jlwm5d"
AuthType Basic
AuthName "This is area 51"
AuthUserFile /etc/apache2/.htpasswd
Require valid-user
```

Save the file.

---

# Step 13: Restart Apache2

**Bash**

```bash id="jlwm44"
service apache2 restart
```

**Explanation:**
Reloads Apache with the updated authentication settings.

---

# Step 14: Test Password Protection

Open the browser and access:

```text id="jlwm9v"
http://localhost/DOCS
```

A login popup appears requesting:

* Username : aayush
* Password : < the password you created during htpasswd setup.>

Enter the credentials created using `htpasswd`.

---
# Authentication Workflow

1. User accesses protected directory.
2. Apache checks `.htaccess`.
3. Apache verifies credentials from `.htpasswd`.
4. If authentication succeeds, access is granted.

---
# Applications of Apache Authentication

* Protecting confidential documents
* Restricting admin panels
* Internal company portals
* Development environments
* Secure file sharing

---
# Important Notes
* `.htpasswd` should never be publicly accessible.
* Use strong passwords.
* HTTPS is recommended to protect credentials during transmission.
* Authentication works best with SSL/TLS enabled.

---

# Explanation of Technologies Used

### Apache HTTP Server

Hosts and manages web resources.

### `.htpasswd`

Stores encrypted user credentials.

### `.htaccess`

Controls directory-level access rules.

### Basic Authentication

Provides username/password-based access control.

---

