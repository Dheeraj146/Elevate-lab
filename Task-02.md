# Windows Firewall
1. Open Firewall Configuration Tool
- Press Win + R, type wf.msc, and press Enter to open Windows Defender Firewall with Advanced Security.

2. List Current Firewall Rules
- In the left pane, click Inbound Rules or Outbound Rules to see the list.

3. Add Rule to Block Inbound Traffic on Port 23 (Telnet)
- Right-click Inbound Rules → New Rule →

<pre>
Select Port

Choose TCP → Enter 23

Select Block the connection

Apply to all profiles (Domain, Private, Public)

Name it: Block Telnet
</pre>

4. Test the Rule
- Try to connect using telnet localhost 23 (install Telnet client if needed: dism /online /Enable-Feature /FeatureName:TelnetClient).

- You should see a connection failure.

5. Allow SSH (N/A on Windows unless OpenSSH server is installed)
6. Remove the Test Rule
- Go to Inbound Rules, right-click Block Telnet, and click Delete.

7. Commands/GUI Summary
<pre>
Open with wf.msc

Block: Inbound Rule → Port 23 → Block

Remove: Right-click rule → Delete
</pre>
# Linux (UFW – Uncomplicated Firewall)
1. Open Terminal & Ensure UFW is Installed
<pre>sudo apt install ufw  # Debian/Ubuntu</pre>
2. List Current Firewall Rules

<pre>sudo ufw status numbered</pre>
3. Block Inbound Traffic on Port 23 (Telnet)

<pre>sudo ufw deny 23/tcp</pre>
4. Test the Rule
Try to connect:

<pre>telnet localhost 23</pre>
You should get a connection refused or timeout.

5. Allow SSH on Port 22
<pre>
sudo ufw allow 22/tcp</pre>
6. Remove the Block Rule
<pre>
sudo ufw delete deny 23/tcp</pre>
7. Summary of UFW Commands Used
<pre>
sudo ufw status numbered         # List rules
sudo ufw deny 23/tcp             # Block Telnet
sudo ufw allow 22/tcp            # Allow SSH
sudo ufw delete deny 23/tcp      # Remove test block
  </pre>
# Summary: How Firewalls Filter Traffic
- A firewall monitors and controls incoming and outgoing network traffic based on predefined security rules. It acts as a barrier between a trusted internal network and untrusted external networks:

- Inbound rules: Control what traffic can enter your system.

- Outbound rules: Control what traffic can leave your system.

- Rules can be set for:

<pre>Specific ports (e.g., 22, 23)

Specific protocols (TCP/UDP)

Specific IP addresses

Firewalls can:

Allow trusted connections

Block harmful traffic

Limit exposure to specific services (e.g., SSH)
  </pre>
