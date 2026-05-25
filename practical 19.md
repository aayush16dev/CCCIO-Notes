
---

# **Hosting Your Website Using GitHub Pages (`username.github.io`)**

---

## **Overview**

GitHub Pages allows you to host a static website **for free** directly from your GitHub repository.  
This practical demonstrates how to deploy a personal website using the **`username.github.io`** repository.

---

## **Key Components**

- **GitHub Account** – Hosting platform
- **GitHub Pages** – Free static web hosting service
- **Repository** – Stores website files
- **HTML / CSS** – Website content

---

## **Step‑by‑Step Procedure**

---

### **1. Create a GitHub Account**

1. Open: **[https://github.com](https://github.com/)**
2. Create an account and verify your email.

---

### **2. Create Repository**

1. Click **New Repository**
2. Repository name must be:

```
username.github.io
```

> Replace `username` with your GitHub username exactly.

3. Set repository as **Public**
4. Click **Create Repository**

---

### **3. Upload Website Files**

Click **Add file → Upload files**  
Upload:

- `index.html`
- `style.css` (optional)
- images or other assets

Example `index.html`:

```html
<!DOCTYPE html>
<html>
<head>
<title>My GitHub Website</title>
</head>
<body>
<h1>Welcome to My Website</h1>
<p>This site is hosted on GitHub Pages.</p>
</body>
</html>
```

Click **Commit changes**

---

### **4. Enable GitHub Pages**

1. Open your repository
2. Go to **Settings → Pages**
3. Under **Source** select:

```
Deploy from a branch
```

4. Branch:

```
main
```

5. Folder:

```
/ (root)
```

6. Click **Save**

---

### **5. Access Your Website**

After 1–2 minutes, your website will be live at:

```
https://username.github.io
```

---

### **6. Test and Update**

Edit `index.html`, commit changes, and refresh your website to see updates instantly.

---
## **Result**
A personal website is successfully hosted online using **GitHub Pages** with the URL:

```
https://username.github.io
```

---

