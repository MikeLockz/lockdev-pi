# lockdev-pi

## Flash pi
Download image
https://www.raspberrypi.org/downloads/raspbian/

Flash with etcher
https://www.balena.io/etcher/

## Enable ssh

create file named `ssh` in root of sd card

## Set static IP

```bash
sudo nano /etc/dhcpcd.conf
```

## Update configuration

```bash
interface eth0
static ip_address=192.168.0.21/24
static routers=192.168.0.1
static domain_name_servers=192.168.0.1 8.8.8.8 fd51:42f8:caae:d92e::1
```

## Update pi

```bash
sudo apt-get install git
```

## Install docker

```bash
sudo apt-get install git
git clone https://github.com/gcgarner/IOTstack.git ~/IOTstack
cd ~/IOTstack
./menu.sh
```

Follow prompts to install docker. Restart.

## Install portainer and pihole

```bash
./menu.sh
```

Build stack and follow prompts.

## Install OpenVPN
- Generate .ovpn 
- Copy .ovpn from pi
- Copy .ovpn to device
- Install .ovpn on device

Install OpenVPN monitor
- http://openvpn-monitor.openbytes.ie/#docker
