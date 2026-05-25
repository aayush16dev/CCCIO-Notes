
---

# **Establishing Proxy using TOR & ProxyChains**

---

## **Overview**

This practical demonstrates how to route your internet traffic through the **Tor network** using **ProxyChains** on Kali Linux.  
The goal is to **hide your real IP address**, improve anonymity, and enhance privacy by passing traffic through multiple anonymous relays.

---

## **Key Components**

|Component|Purpose|
|---|---|
|**Kali Linux**|Operating system|
|**ProxyChains**|Forces applications to use proxy servers|
|**Tor**|Anonymous network that hides the source of traffic|

---

## **Step-by-Step Procedure**

---

### **1. Install ProxyChains**

Update package list:

```bash
apt update
```

Install ProxyChains:

```bash
apt install proxychains
```

---

### **2. Configure ProxyChains**

Open the configuration file:

```bash
mousepad /etc/proxychains.conf
```

Find and modify these lines:

```conf
strict_chain
socks4 127.0.0.1 9050
socks5 127.0.0.1 9050
```

**Explanation:**

- `strict_chain` → Forces all traffic through the proxy chain
- `127.0.0.1 9050` → Tor's local SOCKS proxy address
- Port **9050** is the default Tor proxy port

Save and exit.

---

### **3. Start the Tor Service**

```bash
systemctl start tor
```

Verify Tor is running:

```bash
systemctl status tor
```

---

### **4. Route Applications Through Tor**

Run any program through ProxyChains by adding `proxychains` before the command:

```bash
proxychains firefox
```

Now Firefox traffic is routed through the **Tor network**.

---

## **Verification (Optional)**

Check your public IP:

```bash
proxychains curl ifconfig.me
```

Your IP should now be different from your real one.

---

## **Key Points**

- Provides **strong anonymity** by masking real IP address
- Useful for **privacy, reconnaissance, and penetration testing**
- Slows down traffic due to multiple relay hops (expected behavior)
- Should always be used **ethically and legally**

---
