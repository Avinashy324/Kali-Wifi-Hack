# WiFi WPA Handshake Capture & Security Assessment

## Overview

This project demonstrates how WPA/WPA2 wireless authentication works and how weak passwords can compromise network security. The experiment was performed using Kali Linux and the Aircrack-ng suite during Hackathon Phase 1 at KL University.

The goal is to capture WPA handshake packets and perform password strength analysis.

## Tools Used

* Kali Linux
* Aircrack-ng Suite
* Airmon-ng
* Airodump-ng
* Aireplay-ng

## Project Workflow

### 1. Enable Monitor Mode

The wireless adapter was switched to monitor mode to capture raw network packets.

```
sudo airmon-ng start wlan0
```

### 2. Scan Available Networks

Nearby wireless networks were scanned to identify targets and monitor their traffic.

```
sudo airodump-ng wlan0
```

### 3. Capture WPA Handshake

A specific network was monitored to capture the WPA authentication handshake.

### 4. Deauthentication Test

Aireplay-ng can be used to trigger reconnection events so the handshake can be captured.

### 5. Password Security Testing

Aircrack-ng tests captured handshakes against a password list.

```
aircrack-ng capture.cap -w wordlist.txt
```

## Learning Outcomes

* Wireless network packet monitoring
* WPA/WPA2 authentication understanding
* Ethical penetration testing workflow
* Importance of strong WiFi passwords

## Disclaimer

This project was conducted in a controlled lab environment strictly for educational and ethical cybersecurity research.
