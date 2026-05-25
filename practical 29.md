
---

# **The Curl Tool**

## **Objective**

To understand and demonstrate the usage of the `curl` command-line tool for data transfer using different HTTP methods (GET, POST) and options.

---

## **1. Introduction to Curl**

`curl` is a command-line tool used for transferring data with URLs. It supports various protocols like HTTP, HTTPS, FTP, SCP, and many more. It allows users to send requests and receive responses using different HTTP methods.

---

## **2. Installation of Curl**

To install `curl` on a Linux-based system, use:

```bash
sudo apt install curl
```

To verify the installation:

```bash
curl --version
```

---

## **3. Sending a GET Request**

A `GET` request is used to fetch data from a server. By default, `curl` sends a `GET` request.

### **Steps:**

1. Open the terminal.
2. Execute the following command:
    
    ```bash
    curl www.google.com
    ```
    
3. Observe the response, which will be the HTML content of Google’s homepage.

### **Saving the Response to a File**

To save the response to a file:

```bash
curl -o google.html https://www.google.com
```

Now, view the file using:

```bash
cat google.html
```

---

## **4. Sending a Custom GET Request**

To explicitly specify the `GET` method:

```bash
curl --request GET https://www.google.com
```

---

## **5. Sending a POST Request**

A `POST` request is used to send data to a server.

### **Steps:**

4. Create an `index.html` file:
    
    ```html
    <!DOCTYPE html>
    <html>
    <body>
        <form action="postmethod.php" method="post">
            Username: <input type="text" name="username" /><br>
            Area of Study: <input type="text" name="area" /><br>
            <input type="submit" />
        </form>
    </body>
    </html>
    ```
    
5. Create a `postmethod.php` file:
    
    ```php
    <!DOCTYPE html>
    <html>
    <body>
        Welcome <?php echo $_POST["username"]; ?> <br>
        Your Area of Study is: <?php echo $_POST["area"]; ?>
    </body>
    </html>
    ```
    
6. Start a local server to handle the PHP request.
7. Use `curl` to send a `POST` request:
    
    ```bash
    curl --request POST --data "username=John&area=Cybersecurity" http://localhost/postmethod.php
    ```
    

---

## **6. Difference Between GET and POST**

|Feature|GET Request|POST Request|
|---|---|---|
|Data Location|URL Parameters|Request Body|
|Security|Less Secure (visible in URL)|More Secure (hidden in body)|
|Data Limit|Limited|Can send large data|
|Bookmarkable|Yes|No|

---

## **7. Additional Curl Commands**

### **Using Curl with Authentication**

For basic authentication:

```bash
curl -u username:password https://example.com
```

### **Uploading a File with Curl**

To upload a file:

```bash
curl -F "file=@example.txt" https://example.com/upload
```

---
