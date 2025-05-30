# 1. Insta l OpenVAS or Nessus Essentials.

##LINUX
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
