Mobile PiHole VPN - protected by WireGuard.

This is a (semi) comprehensive tutorial on how to setup WireGuard on Ubuntu, and then setup a basic PiHole server that only listens on the client WireGuard subnet. This guide expects you to have moderate experience with any Linux distro, particularly Ubuntu, and also to have a basic understanding of what PiHole and WireGuard do and how they work (in a general sense, at least). This guide is up to date as of 01/16/2021, and is using Ubuntu 20.04 and the latest versions of WireGuard in the repo, and PiHole as of this date.

First things first - get yourself a VM or VPS. I've used Digital Ocean for years, mainly because I enjoy their user interface. After doing the initial install of Ubuntu, and updating all packages, jump into the root user and install PiHole using this command:

curl -sSL https://install.pi-hole.net | bash
(obtained from https://github.com/pi-hole/pi-hole/#one-step-automated-install)


WireGuard using this command:

wget https://git.io/wireguard -O wireguard-install.sh && bash wireguard-install.sh

This command is using the wonderful script written by Nyr. This will setup WireGuard, and will provide an easy to use interface for adding new devices to your server. It will ask you which IPv4 address it should use - pick the one that is not a private address. On both servers that I have setup recently, it is the first option. It will then ask for the port - I allowed it to use the default, 51820. Then, it will ask for a first client name - I'm using ba-iphone. For the DNS resolver, use the system resolver. As the system resolver is not PiHole right now, we will have to change the value of the first client's DNS. We will fix this for the future.

<insert pic>

Anytime you add a client with this script, including upon first run, it will generate both a QR code and a config file.
