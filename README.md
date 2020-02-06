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

https://github.com/gcgarner/IOTstack/wiki/Getting-Started

## Install portainer and pihole

```bash
./menu.sh
```

Build stack and follow prompts.

## Install OpenVPN
### Add docker-compose details

https://github.com/kylemanna/docker-openvpn/blob/master/docs/docker-compose.md

```bash
nano ~/IOTstack/docker-compose.yml
```

and add below other services

```bash
services:
  openvpn:
    cap_add:
     - NET_ADMIN
    image: darathor/openvpn
    container_name: openvpn
    ports:
     - "1194:1194/udp"
    restart: always
    volumes:
     - ./openvpn-data/conf:/etc/openvpn
```

https://github.com/OpenVPN/openvpn/tree/master/sample/sample-config-files

- Generate .ovpn 
- Copy .ovpn from pi
- Copy .ovpn to device
- Install .ovpn on device
https://tunnelblick.net/downloads.html

Install OpenVPN monitor
- http://openvpn-monitor.openbytes.ie/#docker
