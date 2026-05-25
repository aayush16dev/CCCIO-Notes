# Practical: Observing the Use of Seeker with Ngrok in Kali Linux

Seeker is an open-source tool for creating phishing payloads, which can be used for educational purposes. It generates a malicious link that you can share with a target. Once the target clicks on the link, the tool can capture information about the victim's device, including geolocation, device details, and more.

Ngrok is used to expose your local server to the public internet, making it easy to test and demonstrate web applications or payloads in a secure way.

---

## **Key Steps**

### **Step 1: Install Dependencies**

Before starting, ensure you have installed all the required dependencies.

1. **Install Seeker**: Clone the Seeker repository and install the necessary dependencies.
    
    ```bash
    git clone https://github.com/thewhiteh4t/seeker.git
    cd seeker
    pip3 install -r requirements.txt
    ```

2. **Set up Ngrok**: Start Ngrok to forward the HTTP traffic to your local machine. You will need an Ngrok account for the authentication token.

    ```bash
    ./ngrok config authtoken YOUR_NGROK_AUTH_TOKEN
    ./ngrok http 8080
    ```

---

### **Step 2: Launch Seeker**

1. **Start Seeker**: Navigate to the Seeker directory and run the tool.
    
    ```bash
    cd seeker
    python3 seeker.py
    ```
    
2. **Configure the Payload**: After Seeker starts, it will display a menu. Follow these steps:
    
    - Choose the option to **Generate Payload**.
    - You will need to provide a domain (use the Ngrok URL you obtained earlier, which will look like `http://xyz.ngrok.io`).
    - Set up the desired configuration (e.g., location spoofing, device details, etc.).
3. **Generate the Malicious Link**: Once the payload is generated, Seeker will provide you with a phishing link. This is the URL you will share with the target.
    

---

### **Step 3: Observe Incoming Data**

1. **Access the Seeker Web Panel**:
    
    - Seeker will provide a local web interface, typically accessible at `http://127.0.0.1:5000`.
    - You can also access this panel remotely via the Ngrok URL that you set up earlier (`http://xyz.ngrok.io`).
2. **Monitor the Payload Interaction**:
    
    - When the victim clicks the link, their data (IP address, device details, location, etc.) will be shown in the Seeker interface.
    - The victim's location and device data can be monitored in real time, and their details will be captured and displayed on the Seeker dashboard.

---

### **Basic Observation**

- **Ngrok Tunnel**: Ngrok allows you to make your local Kali machine accessible to the public internet, enabling you to host the phishing payload securely. Ngrok assigns a random subdomain to your local server, making it publicly available.
    
- **Seeker Payload**: The Seeker tool generates a phishing URL that you can send to the target. Once they interact with the payload, it starts capturing data.
    
- **Captured Data**: Seeker shows the victim’s IP, geolocation, operating system, browser, and device details in the web interface. You can monitor these details as they come in.
    

---

### **Important Notes to Remember**
    
4. **Localhost Access**: The Seeker web interface will only be accessible to your local machine unless exposed via Ngrok. Always remember to properly configure and authenticate access when sharing links with others.
    
5. **Data Privacy**: Ensure that all captured data is handled responsibly. Do not misuse any personal data or information captured via the phishing attack.
    

---

