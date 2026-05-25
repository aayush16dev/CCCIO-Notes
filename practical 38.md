## Practical Guide for Using CamPhish

CamPhish is a phishing tool specifically designed to capture images from the front camera of a target device. It achieves this by hosting a fake webpage that requests camera access. This practical guide will walk you through the installation and usage of CamPhish. **It is crucial to understand that using CamPhish without the explicit consent of the target is illegal and unethical. This guide is for educational purposes only to demonstrate how such attacks work, enabling better defense strategies.**

**Objective:** Understand how CamPhish works and how to defend against it. (For educational purposes only.)

**Prerequisites:**

- A Kali Linux system (or any Linux distribution with Python 3 and ngrok).
- Internet connectivity.
- Basic understanding of Linux commands and web technologies.

**Steps:**

_Explanation:_ CamPhish is written in Python, so you need Python 3 and the package installer `pip`.

1. **Install `ngrok`:**
    
    - Download `ngrok` from their official website: [https://ngrok.com/download](https://www.google.com/url?sa=E&source=gmail&q=https://ngrok.com/download)
        
    - Unzip the downloaded file.
        
    - Move the `ngrok` executable to a directory in your PATH (e.g., `/usr/local/bin`):
        
        Bash
        
        ```
        sudo mv ngrok /usr/local/bin
        ```
        
    - Authenticate `ngrok` (you'll need to create an account on their website):
        
        Bash
        
        ```
        ngrok authtoken <your_authtoken>
        ```
        

_Explanation:_ `ngrok` creates a secure tunnel to your local machine, making the CamPhish webpage accessible over the internet.

2. **Clone the CamPhish repository:**

<!-- end list -->

Bash

```
git clone https://github.com/techchipnet/CamPhish.git
cd CamPhish
```

_Explanation:_ Downloads the CamPhish tool from GitHub and navigates into the directory.

3. **Install the required Python packages:**

<!-- end list -->

Bash

```
pip3 install -r requirements.txt
```

_Explanation:_ Installs the necessary Python libraries that CamPhish depends on.

4. **Run CamPhish:**

<!-- end list -->

Bash

```
python3 camphish.py
```

_Explanation:_ Executes the main Python script.

5. **Choose a template:**
    
    CamPhish offers different webpage templates. Select the one you want to use. The templates are designed to mimic common login or verification pages to trick the target.
    
6. **`ngrok` setup:**
    
    CamPhish will automatically start `ngrok`. It will provide you with a URL (e.g., `https://xxxxxxx.ngrok.io`). This is the link you will send to the target.
    
7. **Social Engineering:**
    
    This is the most crucial part of a phishing attack. You need to convince the target to click on the `ngrok` link. Attackers often use deceptive emails, messages, or other social engineering tactics to trick the target.
    
8. **Capturing the image:**
    

If the target clicks the link and grants camera access, CamPhish will capture an image from their front camera and display it on your terminal.

**Explanation of Functionality:**

CamPhish works by creating a fake webpage that requests access to the user's camera. When the target visits the link, their browser will prompt them to allow the website to use the camera. If they grant permission, the JavaScript code in the webpage captures an image and sends it to the attacker's server (your local machine, tunneled through `ngrok`).


**Example Scenario (for educational purposes only):**

You are testing the security of your own network.

9. Run CamPhish.
10. Send the `ngrok` link to a test device (that you own or have permission to test on).
11. Observe the image capture on your Kali machine.
