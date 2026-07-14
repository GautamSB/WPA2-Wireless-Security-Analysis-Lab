# WPA2 Wireless Security Assessment Report

## Project Overview

This project demonstrates a complete WPA2 wireless security assessment performed in a controlled laboratory environment using Kali Linux and the Aircrack-ng suite. The objective of this lab was to understand the process of configuring a wireless adapter for monitor mode, capturing a WPA2 four-way handshake, performing an offline dictionary attack against the captured handshake, and restoring the system to its normal operating state.

> **Disclaimer:** This assessment was performed only against an authorized wireless network created for educational purposes. No unauthorized networks or devices were targeted.

---

# Objectives

- Configure a compatible USB wireless adapter.
- Enable monitor mode.
- Discover nearby wireless access points.
- Identify the target wireless network.
- Monitor connected wireless clients.
- Capture the WPA2 Four-Way Handshake.
- Demonstrate offline password recovery using a dictionary attack.
- Restore normal wireless networking after completing the assessment.

---

# Lab Environment

| Component | Details |
|-----------|---------|
| Operating System | Kali Linux |
| Virtualization | VMware Workstation |
| Wireless Adapter | Realtek RTL8188EUS USB Adapter |
| Wireless Toolkit | Aircrack-ng Suite |
| Wordlist | Custom Dictionary |
| Wireless Security | WPA2-PSK |
| Network Type | Authorized Home Lab |

---

# Tools Used

- Kali Linux
- VMware Workstation
- Aircrack-ng
- Airmon-ng
- Airodump-ng
- Aireplay-ng
- Aircrack-ng
- Systemctl

---

# Lab Methodology

## Step 1 – Connecting the Wireless Adapter

A compatible USB wireless adapter was connected directly to the Kali Linux virtual machine through VMware Workstation.

**Purpose**

To provide direct access to wireless hardware capable of monitor mode and packet injection.

**Screenshot**

`01-usb-wifi-adapter-connected.png`

---

## Step 2 – Preparing the Wireless Interface

The wireless adapter was verified using Aircrack-ng and interfering network processes were terminated.

### Command

```bash
airmon-ng

airmon-ng check kill
```

**Purpose**

Preparing the wireless interface for monitor mode by stopping processes that could interfere with packet capture.

**Screenshot**

`02-kill-network-processes.png`

---

## Step 3 – Enabling Monitor Mode

The wireless adapter was switched into monitor mode.

### Command

```bash
airmon-ng start wlan0
```

**Purpose**

Monitor mode allows passive capture of IEEE 802.11 wireless frames without associating with an access point.

**Screenshot**

`03-enabled_monitor-mode.png`

---

## Step 4 – Discovering Wireless Networks

Nearby wireless access points were identified.

### Command

```bash
airodump-ng wlan0
```

**Purpose**

Identify available wireless networks along with:

- BSSID
- Channel
- Encryption
- Authentication
- Signal Strength
- ESSID

**Screenshot**

`04-discovered-access_points.png`

---

## Step 5 – Monitoring the Target Access Point

The selected access point was monitored continuously.

### Command

```bash
airodump-ng --bssid <Target-BSSID> --channel <Channel> -w capture wlan0
```

**Purpose**

Capture packets from the authorized target network and monitor connected wireless clients while waiting for a WPA2 Four-Way Handshake.

**Screenshot**

`05-target-access-point-monitoring.png`

---

## Step 6 – Capturing the WPA2 Four-Way Handshake

Deauthentication frames were transmitted to prompt a client to reconnect, generating a WPA2 Four-Way Handshake.

### Command

```bash
aireplay-ng --deauth 100 -a <Target-BSSID> wlan0
```

**Purpose**

Disconnect a connected client so it automatically reconnects, allowing the handshake to be captured by the monitoring interface.

**Screenshot**

`06-deauthentication-request-sent.png`

---

## Step 7 – Handshake Capture

After the client reconnected, the WPA2 Four-Way Handshake was successfully captured.

The Aircrack-ng suite confirmed handshake capture.

**Purpose**

The handshake provides the authentication exchange required for offline password verification.

**Screenshot**

`07-WPA2-fourway-handshake-captured.png`

---

## Step 8 – Offline Dictionary Attack

The captured handshake was analyzed using Aircrack-ng with a custom dictionary.

### Command

```bash
aircrack-ng capture-01.cap -w wordlist.txt
```

**Purpose**

Perform an offline dictionary attack against the captured handshake to demonstrate WPA2 password recovery in an authorized environment.

The correct passphrase was successfully identified from the supplied wordlist.

**Screenshot**

`08-password-recovered-aircrack-ng.png`

---

## Step 9 – Restoring the Network

After completing the assessment, normal networking was restored.

### Commands

```bash
systemctl restart NetworkManager

systemctl status NetworkManager
```

**Purpose**

Restart the NetworkManager service and return the wireless adapter to its standard managed mode for normal connectivity.

**Screenshot**

`09-restored-network.png`

---

# Results

The laboratory assessment successfully demonstrated:

- Successful USB wireless adapter configuration.
- Wireless monitor mode activation.
- Discovery of nearby wireless access points.
- Identification of connected wireless clients.
- Successful capture of the WPA2 Four-Way Handshake.
- Successful offline recovery of the WPA2 passphrase using a dictionary attack.
- Restoration of standard network functionality after the assessment.

---

# Skills Demonstrated

- Wireless Network Security
- WPA2 Authentication
- IEEE 802.11 Fundamentals
- Monitor Mode Configuration
- Wireless Packet Capture
- Four-Way Handshake Analysis
- Dictionary Attack Demonstration
- Linux Command Line
- Aircrack-ng Suite
- Network Troubleshooting
- VMware Workstation
- Cybersecurity Lab Documentation

---

# Key Learning Outcomes

This laboratory exercise provided practical experience with the WPA2 authentication process and demonstrated how weak or predictable passwords can be vulnerable to offline dictionary attacks after a handshake has been captured. It also reinforced the importance of using strong passphrases and performing wireless security assessments only within authorized environments. The exercise improved hands-on proficiency with the Aircrack-ng suite, wireless packet analysis, monitor mode configuration, and professional cybersecurity documentation.

---

# Conclusion

The WPA2 Wireless Security Assessment Lab successfully demonstrated the complete workflow involved in assessing the security of an authorized WPA2-protected wireless network. The assessment included wireless adapter preparation, monitor mode configuration, wireless network discovery, client monitoring, handshake capture, offline password recovery using a dictionary attack, and restoration of normal networking services.

This project strengthened practical understanding of wireless penetration testing methodologies while emphasizing responsible and ethical security testing practices.
