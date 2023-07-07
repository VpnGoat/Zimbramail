# Zimbramail 
Step 1: Update and upgrade existing packages
apt upgrade 
apt upgrade –y
Step 2: Change hostname
hostnamectl set-hostname [your_domain_name]
+config host
vi /etc/hosts
127.0.0.1       localhost
127.0.1.1       ubuntu
[Your IP]   [Your Hostname] mail
#**Step 3: Install DNS server**
+first run some commant befor install
systemctl disable systemd-resolved
systemctl stop systemd-resolved
rm /etc/resolv.conf
sh -c 'echo nameserver 8.8.8.8 >> /etc/resolv.conf'
apt install dnsmasq
+config dnsmasq
vi /etc/dnsmasq.conf
server=8.8.8.8
domain=mail.[hostnam]
mx-host=[hostnam],mail.[hostnam],5
listen-address=127.0.0.1
systemctl restart dnsmasq

**Step 4: Downloading and installing Zimbra Collaboration Tool**

wget -c https://files.zimbra.com/downloads/8.8.15_GA/zcs-8.8.15_GA_4179.UBUNTU20_64.20211118033954.tgz

tar -xvzf zcs-8.8.15_GA_4179.UBUNTU20_64.20211118033954.tgz
cd zcs-8.8.15_GA_4179.UBUNTU20_64.20211118033954
./install.sh


To accept the accompanying Software License agreement, press y. Then press y again to install using Zimbra's package repository.

Except for zimbra-imapd, which is beta-only and not installed by default, type y to install all of the packages.

After being informed that changes will be made to the system, choose y to proceed with the installation.

When setup is complete, you'll see this screen and be prompted to set up any remaining objects.

Here, we shall set the unconfigured administrator password for Zimbra. The Admin Password is likewise shown as * in the zimbra-store section. To access the zimbra-store area, press 7 on your keyboard.

Now configure the Admin Password by pressing 4. You will be requested to set the admin password. Enter any passphrase (with a minimum of 6 characters).

Now, press a to apply the settings, then press y again to save the settings. When prompted that the system will be updated, press y.

Now that the setting is complete, you will get the following page; press Enter to go.

Now, the Zimbra mail server installation is complete.

systemctl start imap.service
