#  Network Traffic Capture & Protocol Analysis with Wireshark
## Objective
- Capture live network traffic using Wireshark, identify at least three network protocols, and analyze the types of communication captured.

## Tools Used
- Wireshark v4.4.7
- Operating System: Windows 10 / Linux (Ubuntu) 
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
   - [pcap file](w.pcapng)
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

## Useful Wireshark Display Filters
<pre>
| **Filter**                                 | **Description**                                            |                                            
| ------------------------------------------ | ---------------------------------------------------------- | 
| `ip.addr == 10.0.0.1`                      | Show all traffic with 10.0.0.1 as source or destination    |                                            
| `ip.addr == 10.0.0.0/24`                   | Show all traffic to/from any address in 10.0.0.0/24 subnet |                                            
| `ip.src == 10.0.0.1 && ip.dst == 10.0.0.2` | Traffic from 10.0.0.1 to 10.0.0.2                          |                                            
| `!(ip.addr == 10.0.0.1)`                   | Exclude all traffic to/from 10.0.0.1                       |                                            
| `icmp.type == 3`                           | ICMP “destination unreachable” packets                     |                                            
| `tcp or udp`                               | Show all TCP or UDP traffic                                |                                            
| `tcp.port == 80`                           | Show HTTP traffic (port 80)                                |                                            
| `tcp.srcport < 1000`                       | TCP traffic from ports < 1000                              |                                            
| `!(tcp or udp)`                            | Show non-TCP/UDP traffic                                   |                                            
| `http or dns`                              | Show HTTP or DNS traffic                                   |                                            
| `tcp.flags.syn == 1`                       | TCP packets with SYN flag                                  |                                            
| `tcp.flags == 0x012`                       | TCP packets with SYN and ACK flags                         |                                            
| `tcp.analysis.retransmission`              | Show retransmitted TCP packets                             |                                            
| `http.request.method == "GET"`             | Show HTTP GET requests                                     |                                            
| `http.response.code == 404`                | Show HTTP 404 errors                                       |                                            
| `http.host == "www.test.com"`              | HTTP traffic to specified host                             |                                            
| `tls.handshake`                            | Show only TLS handshake traffic                            |                                            
| `tls.handshake.type == 1`                  | TLS Client Hello packets only                              |                                            
| `dhcp and ip.addr == 10.0.0.0/24`          | DHCP traffic in 10.0.0.0/24                                |                                            
| `dhcp.hw.mac_addr == 00:11:22:33:44:55`    | DHCP for specific MAC address                              |                                            
| `dns.qry.name contains "cnn.com"`          | DNS queries for cnn.com                                    |                                            
| `dns.resp.name contains "cnn.com"`         | DNS responses with cnn.com                                 |                                            
| `frame contains "keyword"`                 | Packets that contain a specific string                     |                                            
| `frame.len > 1000`                         | Packets larger than 1000 bytes                             |                                            
| `eth.addr == 00:11:22:33:44:55`            | Traffic from/to specific MAC address                       |                                            
| `eth[0x47:2] == 01:80`                     | Match Ethernet frames by bytes at offset                   |                                            
| `!(arp or icmp or stp)`                    | Filter out ARP, ICMP, STP (background) traffic             |                                            
| `vlan.id == 100`                           | Packets with VLAN ID 100                                   |                                            

</pre>

  
