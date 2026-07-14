# Screenshots

This directory contains screenshots captured during the **WPA2 Wireless Security Lab**. These screenshots document the complete workflow, including wireless adapter configuration, monitor mode activation, wireless network discovery, target access point monitoring, WPA2 handshake capture, passphrase recovery using a dictionary attack in a controlled environment, and restoration of normal network connectivity.

> **Note:** Sensitive information such as SSIDs, BSSIDs, MAC addresses, and passwords should be blurred or redacted before publishing this repository publicly.

---

## Screenshot List

### 01-usb-wifi-adapter-connected.png
Shows the external USB wireless adapter connected to the Kali Linux virtual machine and detected by the operating system for wireless security testing.

---

### 02-kill-network-processes.png
Displays the termination of interfering network services using `airmon-ng check kill` to prepare the wireless interface for monitor mode.

---

### 03-enabled_monitor-mode.png
Shows the wireless adapter successfully switched to **Monitor Mode**, enabling passive capture of IEEE 802.11 wireless traffic.

---

### 04-discovered-access_points.png
Displays nearby wireless access points discovered using `airodump-ng`, including details such as BSSID, channel, encryption type, authentication method, signal strength, and ESSID.

---

### 05-target-access-point-monitoring.png
Shows continuous monitoring of the selected wireless access point along with connected client devices while waiting for a WPA2 Four-Way Handshake.

---

### 06-deauthentication-request-sent.png
Displays deauthentication frames being transmitted to disconnect connected clients, prompting them to reconnect and generate a WPA2 Four-Way Handshake for capture.

---

### 07-WPA2-fourway-handshake-captured.png
Confirms successful capture of the WPA2 Four-Way Handshake between the authorized wireless client and the access point.

---

### 08-password-recovered-aircrack-ng.png
Shows successful recovery of the WPA2 pre-shared key using **Aircrack-ng** and a dictionary attack against the captured handshake.

> **Note:** This demonstration was performed only against an authorized lab network for educational and cybersecurity training purposes.

---

### 09-restored-network.png
Shows the **NetworkManager** service restarted after the assessment, restoring the wireless interface to normal managed mode and re-enabling standard network connectivity.

---

## Lab Workflow

1. Connect the USB wireless adapter.
2. Terminate interfering network processes.
3. Enable Monitor Mode.
4. Discover nearby wireless networks.
5. Monitor the target access point.
6. Generate and capture the WPA2 Four-Way Handshake.
7. Recover the WPA2 passphrase using a dictionary attack.
8. Restore normal network services and connectivity.

---

**Total Screenshots:** 09
