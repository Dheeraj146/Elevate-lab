# 1. Install OpenVAS 

## LINUX
OpenVAS comes pre-installed in most Kali images, but here's the full setup:
 Step-by-step:
 1. Update system
<pre>sudo apt update && sudo apt upgrade -y</pre>
 2. Install OpenVAS
<pre>sudo apt install openvas -y</pre>
 3. Initialize OpenVAS
<pre>sudo gvm-setup</pre>
This will take some time. It downloads vulnerability data.

 4. Start OpenVAS services
<pre>
sudo gvm-check-setup
sudo gvm-start

</pre>
 4. Access Web UI
<pre>sudo gvm-manage-certs -a
sudo gvm-cli --gmp-username admin --gmp-password yourpassword
</pre>

# Install Nessus Essentials

## On Windows

Step-by-step:
 1. Download Nessus Essentials

<pre>Go to: https://www.tenable.com/products/nessus/nessus-essentials</pre>
Choose "Windows" and download installer

 2. Run Installer
Double-click the .exe file

Follow prompts to complete installation

 3. Start Nessus Service

It runs as a local service and opens browser:
<pre>https://localhost:8834</pre>

 4. Register Nessus Essentials

Choose "Nessus Essentials"

Enter name/email to get activation code

Paste it when prompted

 5. Download Plugins

Let Nessus download and install plugins (~15-20 min)

6.Create a User Account

Set username/password to log in

 7. Begin Scanning

## Linux
Step-by-step:
 1. Download Nessus .deb Package

<pre>Go to: https://www.tenable.com/downloads/nessus</pre>

Choose Debian/Kali

 2. Install Nessus
<pre>sudo dpkg -i Nessus-*.deb
sudo systemctl start nessusd
sudo systemctl enable nessusd
</pre>

 3. Access Web Interface

Open browser:

arduino
<pre>https://localhost:8834</pre>

 4. Register & Activate

Same process as Windows

 5. Wait for Plugin Sync




