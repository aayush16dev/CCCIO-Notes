# how to use monitor mode

## Practical: Using Monitor Mode with Key Points and Steps (Commands)

This practical demonstrates how to use monitor mode on a wireless network interface. Monitor mode allows you to capture all wireless traffic, not just traffic directed to your device. This is crucial for network analysis, security auditing, and penetration testing.

## **Key Points:**

- **Prerequisites:** You'll need a wireless network interface card (NIC) that supports monitor mode. Most modern Wi-Fi adapters do. You'll also need root or sudo privileges.
- **Tools:** We'll primarily use `iwconfig`, `airmon-ng`, and `tcpdump` (or `wireshark` if you prefer a GUI). These tools are generally pre-installed on penetration testing distributions like Kali Linux. For other distributions, you might need to install them (e.g., `apt-get install iwconfig airmon-ng tcpdump` on Debian/Ubuntu-based systems).
- **Caution:** Using monitor mode to capture traffic on a network without permission is illegal. Only use these techniques on networks you own or have explicit permission to test.
- **Interface Identification:** It's crucial to identify the correct name of your wireless interface (e.g., wlan0, wlp2s0). Use `iwconfig` to list available interfaces.

## **Steps and Commands:**

1. **Identify your wireless interface:**


```
iwconfig
```

This command will list all wireless interfaces and their status. Identify the one you want to use for monitor mode (e.g., `wlan0`).

2. **Stop any conflicting processes:**

Processes like NetworkManager or wpa_supplicant can interfere with monitor mode. It's best to stop them. `airmon-ng` can help with this:


```
sudo airmon-ng check kill
```

This command identifies and kills conflicting processes.

1. **Put the interface into monitor mode:**


```
sudo airmon-ng start <interface_name>
```

Replace `<interface_name>` with the actual name of your wireless interface (e.g., `wlan0`). This command creates a new monitor interface (often named `wlan0mon` or similar). Note the name of the monitor interface that `airmon-ng` creates; you'll need it later.

2. **Verify monitor mode:**

```
iwconfig <monitor_interface_name>
```

Replace `<monitor_interface_name>` with the name of the monitor interface (e.g., `wlan0mon`). Look for "Mode:Monitor" in the output.

3. **Capture traffic using `tcpdump` (command-line):**


```
sudo tcpdump -i <monitor_interface_name> -w capture.pcap
```

- `-i <monitor_interface_name>`: Specifies the interface to listen on (e.g., `wlan0mon`).
- `-w capture.pcap`: Saves the captured packets to a file named `capture.pcap`. You can choose any filename.

To stop the capture, press Ctrl+C.

4. **Capture traffic using `wireshark` (GUI):**


```
sudo wireshark
```

Wireshark will start. Select the monitor interface (e.g., `wlan0mon`) from the list of interfaces and click "Start capturing packets."

5. **Return to managed mode (optional):**

After you're done capturing traffic, you can return your interface to managed mode:

```
sudo airmon-ng stop <monitor_interface_name>
sudo airmon-ng check kill  # Kill any remaining conflicting processes
sudo ifconfig <original_interface_name> up # Bring the original interface back up
# Restart NetworkManager (or your network management service) if needed:
sudo systemctl restart NetworkManager  # Example for systemd systems
```

**Example:**

```
iwconfig  # Find interface (e.g., wlan0)
sudo airmon-ng check kill
sudo airmon-ng start wlan0  # Creates wlan0mon
iwconfig wlan0mon  # Verify monitor mode
sudo tcpdump -i wlan0mon -w my_capture.pcap  # Capture traffic
# ... (Capture traffic until Ctrl+C) ...
sudo airmon-ng stop wlan0
sudo airmon-ng check kill
sudo ifconfig wlan0 up
sudo systemctl restart NetworkManager
```

This practical provides a basic introduction to using monitor mode. For more advanced techniques, like filtering traffic or working with specific protocols, consult the documentation for `tcpdump`, `wireshark`, and `airmon-ng`. Remember to use these tools responsibly and ethically.