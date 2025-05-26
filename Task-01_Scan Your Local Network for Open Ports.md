# Nmap Network Scan

This repository contains a basic local network scan using Nmap and analysis of results.

## Tasks

1. Installed Nmap from [https://nmap.org](https://nmap.org)
2. Identified local IP range: `192.168.1.0/24`
3. Performed SYN scan:nmap -sS 192.168.1.0/24
4. Saved results as text and HTML
5. Optionally used Wireshark for packet analysis
6. Researched services on open ports
7. Documented potential security risks

---

## Directory Overview

- `results/`: Contains raw scan outputs
- `analysis/`: Notes about open ports and security risks
- `screenshots/`: Optional images from Wireshark
- `local_scan.sh`: Bash script to rerun the scan

