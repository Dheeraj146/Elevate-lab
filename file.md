# Install Nmap
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
