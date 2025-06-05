#  Network Traffic Capture & Protocol Analysis with Wireshark
## Objective
- Capture live network traffic using Wireshark, identify at least three network protocols, and analyze the types of communication captured.

## Tools Used
- Wireshark v4.x
- Operating System: Windows 10 / Linux (Ubuntu) / macOS (any supported version)
- Active network connection (Wi-Fi or Ethernet)

##  Installing Wireshark
### Ubuntu / Debian
<pre>
sudo apt update
sudo apt install wireshark
</pre>
- When prompted:
 - "Should non-superusers be able to capture packets?"
 - Choose Yes to allow members of the wireshark group to capture packets.
- Add your user to the wireshark group:
<pre>sudo usermod -aG wireshark $USER</pre>
- Log out and log back in (or reboot) to apply group changes.

### Windows 
 1. Download Wireshark
 - Go to: https://www.wireshark.org/download.html

 2. Run Installer
 - Accept the license agreement.
 - Install WinPcap or Npcap when prompted:
  - Choose Npcap (recommended) with default options.
  - Make sure "Install Npcap in WinPcap API-compatible Mode" is checked.
 3. Complete Installation
 - Launch Wireshark from the Start menu or desktop.
 4. Post-Installation Check
 - Open Wireshark.
 - Make sure your network interfaces are listed.
 - Try capturing packets from your active interface (e.g., Wi-Fi, eth0).

## Start Capture:
 - Open Wireshark.
 - Selected active interface: Wi-Fi (could also be eth0 or similar).
 - Clicked Start Capture.

 1. Generate Traffic:
 - Opened a browser and visited https://google.com.
 - Performed a ping to 8.8.8.8 (Google DNS).
 2. Stop Capture:
 - Waited approximately 60 seconds.
 - Clicked Stop to end capture.
 3. Filter Packets:
 - Used display filters:
  - http – to inspect HTTP traffic.
  - dns – to view DNS resolution.
  - tcp – to view transport-layer packets.

## Protocols Identified
1. DNS (Domain Name System)
 - Filter: dns
 - Purpose: Resolves domain names to IP addresses.
 - Example:
   - Query: google.com
   - Response: 93.184.216.34
2. HTTP (HyperText Transfer Protocol)
 - Filter: http
 - Purpose: Web communication protocol.
 - Example:
   - GET /index.html HTTP/1.1
   - Host: google.com

3. TCP (Transmission Control Protocol)
 - Filter: tcp
 - Purpose: Reliable transport protocol for HTTP, DNS, etc.
 - Example:
   - TCP 3-way handshake observed: SYN, SYN-ACK, ACK
   - Port 80 (HTTP), Port 443 (HTTPS)

## [pcap file]()
  
