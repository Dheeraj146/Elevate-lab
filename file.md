# 1. Install Nmap
## Windows

1. Go to the official Nmap website: https://nmap.org/download.html.
   Under “Microsoft Windows binaries,” click the installer link (e.g., nmap-<version>-setup.exe).
2. Run the Installer:
   Double-click the downloaded .exe file.
   Choose whether to install Nmap only or also include Zenmap (GUI), Ncat, and Npcap (required for packet capture).
3. Install Npcap:
    Nmap requires Npcap to function.
    The installer typically installs it automatically. Accept the defaults unless you have specific needs (e.g., for Wireshark).
4. Verify Installation:
   Open Command Prompt and type:
<pre>nmap --version</pre>
  You should see version info if the installation succeeded.




## Debian/Ubuntu Linux

Installing Nmap on Kali Linux
Kali Linux usually comes with Nmap pre-installed. But if it's missing or you want to reinstall/update:

1. Using apt (recommended)
Update Package Lists:
<pre>sudo apt update</pre>
2. Install Nmap:
<pre>sudo apt install nmap -y</pre>
3. Verify Installation:
<pre>nmap --version</pre>
 You should see version info if the installation succeeded.

 # 2. Find your local IP range (e.g., 192.168.1.0/24).

## Windows
1. Open Command Prompt:
Press Win + R, type cmd, hit Enter.
<pre>ipconfig</pre>
2. Look for your active network adapter and note: In my case 
IPv4 Address (10.53.17.74)
Subnet Mask (255.255.224.0)
<pre>Wireless LAN adapter Wi-Fi:

   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . : fe80::f0f7:f7c0:c8b7:2923%13
   IPv4 Address. . . . . . . . . . . : 10.53.17.74
   Subnet Mask . . . . . . . . . . . : 255.255.224.0
   Default Gateway . . . . . . . . . : 10.53.0.1
</pre>

4. Determine the IP range:
If your IP is 10.53.17.74 and subnet mask is 255.255.224.0, your range is:
<pre>10.53.0.0/19</pre>

## Debian/Ubuntu Linux
Open Terminal and run:
<pre>ip a</pre>
Find your IP under your network interface (likely eth0 or wlan0):
<pre>inet 192.168.1.5/24</pre>
<pre>eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 00:0c:29:25:f4:5e brd ff:ff:ff:ff:ff:ff
    inet 192.168.159.139/24 brd 192.168.159.255 scope global dynamic noprefixroute eth0
       valid_lft 1661sec preferred_lft 1661sec
    inet6 fe80::f89d:f794:f4db:9c5e/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever</pre>
The /24 is your CIDR range, so the network is:
<pre>192.168.159.139/24</pre>

# Run: nmap -sS 192.168.1.0/24 to perform TCP SYN scan.

## Windows 
nmap -sS -T4 10.53.0.0/19
<pre>Starting Nmap 7.95 ( https://nmap.org ) at 2025-05-26 15:36 India Standard Time
Nmap scan report for 10.53.17.74
Host is up (0.00015s latency).
Not shown: 990 closed tcp ports (reset)
PORT     STATE SERVICE
135/tcp  open  msrpc
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
902/tcp  open  iss-realsecure
912/tcp  open  apex-mesh
2869/tcp open  icslap
4343/tcp open  unicall
4449/tcp open  privatewire
8000/tcp open  http-alt
8089/tcp open  unknown

Nmap done: 256 IP addresses (1 host up) scanned in 16.85 seconds</pre>

## Debian/Ubuntu Linux

nmap -sS 192.168.159.139/24
<pre>Starting Nmap 7.95 ( https://nmap.org ) at 2025-05-26 06:47 EDT
Nmap scan report for 192.168.159.2
Host is up (0.00061s latency).
Not shown: 999 closed tcp ports (reset)
PORT   STATE SERVICE
53/tcp open  domain
MAC Address: 00:50:56:E2:9C:FB (VMware)

Nmap scan report for 192.168.159.254
Host is up (0.00064s latency).
All 1000 scanned ports on 192.168.159.254 are in ignored states.
Not shown: 1000 filtered tcp ports (no-response)
MAC Address: 00:50:56:E4:B1:9A (VMware)

Nmap scan report for 192.168.159.139
Host is up (0.000021s latency).
All 1000 scanned ports on 192.168.159.139 are in ignored states.
Not shown: 1000 closed tcp ports (reset)

Nmap done: 256 IP addresses (3 hosts up) scanned in 7.44 seconds</pre>

 
