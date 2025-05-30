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


<pre>https://localhost:8834</pre>

 4. Register & Activate

Same process as Windows

 5. Wait for Plugin Sync


# 2. Set up scan target as your local machine IP or localhost
1. Find Your Local IP Address
### Kali Linux:
<pre>ip a</pre>
Look for inet under your active network interface (e.g., eth0, wlan0). Example: 192.168.1.100

### Windows:
Open Command Prompt:
<pre>ipconfig</pre>
Find your IPv4 Address under the active network adapter. Example: 192.168.1.50

2. Set Up Scan Target in OpenVAS
🌐 Access OpenVAS Web UI:
Open browser and go to:
<pre>https://localhost:9392</pre>
Steps:
 1. Login to OpenVAS

 2. Go to Configuration > Targets

 3. Click "New Target"

 4. Fill in the details:

   - Name: e.g., "Localhost"

     - Hosts:

      - Use 127.0.0.1 for localhost

     - Or your local IP (e.g., 192.168.1.50)

    - Leave the rest as default or adjust as needed

 5. Click Create

 3. Set Up Scan Target in Nessus Essentials
🌐 Access Nessus Web UI:
  1. Open browser:
<pre>https://localhost:8834</pre>
 Steps:
  2. Login to Nessus

  3. Go to My Scans

  4. Click "New Scan" > Basic Network Scan

  5. Fill in the details:

     -Name: e.g., "Scan Localhost"

     - Targets:

      - 127.0.0.1 (loopback)

      - Or 192.168.x.x (your machine's local IP)

  6. Optional: Adjust scan policy settings

  7. Click Save && start the scan

# 3. Start a fu l vulnerability scan
In OpenVAS (Greenbone Vulnerability Management)
🌐 Access Web Interface:
<pre>https://localhost:9392</pre>

 Steps to Start Full Scan:
  1. Login with your OpenVAS credentials.

Go to "Scans" > "Tasks"

  2. Click "New Task"

  3. Fill out the form:

    - Name: e.g., "Full Scan - Localhost"

    - Target: Choose the target you previously created (e.g., 127.0.0.1 or 192.168.x.x)

    - Scan Config: Select Full and fast

  4. Click Create

  5. After it's created, click the play ▶️ icon to start the scan

### Monitor Progress:
The task will change status to Running

May take 30–60 minutes depending on system size and open services



