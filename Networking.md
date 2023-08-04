## IP Address
```
$ `hostname -I` // Give's the IP address, or use
$ `Glasswire` // Use GlassWire to find all IP addresses connected to your host network
$ ifconfig // to check your IP address
$ ipconfig
```

## Restart Network
```
$ sudo service networking restart //restart the local network interfaces
$ sudo systemctl restart network-manager //resets the wifi
```

## Ping
- `Ping` can be used to test connectivity
```
$ ping <IP_Address> // to test connectivity of a certain IP address
$ ping 8.8.8.8
$ ping bitbucket.org
```

## New Hostname
```
$ sudo pifi set-hostname NEWHOSTNAME
```

## Change Hostname
```
$ cd /etc
$ sudo nano hosts # change hostname
$ sudo nano hostname
```

## Wifi 
```
$ route -n // tells you which wifi is connected
```

## Wifi's saved
```
$ nmcli connection
```

## Networking Configurations
```
$ nmcli
$ nmtui
$ nmcli dev wifi connect [SSID] password [password] [hidden yes]
$ pifi
```

## Nmcli
```
$ nmcli c
$ nmcli d status
$ nmcli connection // wifi's saved
```

## nc to Connect
```
$ nc -l 8081
$ nc 127.0.0.1 8081
```

## Network Manager Config
```
$ cd /etc
$ cd NetworkManager
$ nano NetworkManager.conf
$ cd system-connections
$ sudo nano ethernet-connection
```

## Networks Connected
- wlan0
- Eth0
- docker0: this one is a virtual hidden one inside jetbot, used to connect with the ethernet and wifi

## The Ethernet Network is saved at
```
$ cd /etc/network
$ nano interfaces // code will be saved here!
```
- P.S: sometimes it might backup everything into interfaces.swp (swap file) that's used as a backup when interfaces is empty

## The File: `/etc/network/interfaces` should have the following inside of it:
```
 interfaces(5) file used by ifup(8) and ifdown(8)
Include files from /etc/network/interfaces.d:
source-directory /etc/network/interfaces.d
```

## Network Attributes
- Mask: binary term, AND and NOR gates 
- Subnet: 
- Gateway: 

## DNS Server
- Domain Name System (DNS)
- DNS translates domain nmaes to IP addresses so browsers can load internet resources.
- Each device connected to the internet has a unique IP address which other machines used to find the device.
- DNS servers eliminate the need for humans to memorize IP addresses such as 192.168

## Notes
- Running a virtual machine on your windows with Oracle for example, you'll face a lot of networking issues. 
- Bridging the networks from your windows onto virtual machine is quite challenging.. you'll need to change a few things in the settings to make it work.
- IPv4/IPv6
- MQTT: publisher/subscriber communication policy
- A device can have more than one IP address like 2 IP addresses
- When you have an IP address of like 10.10.10.2 it comes with a subnet mask 255.255.255.0 (subnet is the first 3 numbers) and you neede to always to set that subnet early on in order for networks to communicate. It fundamently means that it only can communicate to networks that have the same subnet as we defined. Routers have a smart way of doing it by themselves. It runs as a switch in between them both
- 255.255.255.0 is eqiuvalent to 255.255.255.4/24 or ff.ff.ff.0
- `traceroute IP_Address`: shows you how the cycle of info looks like 
