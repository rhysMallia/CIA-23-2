Suports lean and featured networks managers
	lots of manual configs vs none
	can be turned into routers and firewalls with basic tools

LEgacy network tools
Net-tools package no deprecated, replaced by iproute

Replaced commands ...
arp -> ip neighbour
ifconfig -> ip address, ip link
netstat -> ss
route -> ip route

**view network config**
- ip link : host devices, their status and mac addresses
- ip address : view interfaces
	- ip address show < int >
	- windows equiv is ipconfig
- ip route : view routes for this host
- ip neighbour : view hosts arp table
- View network status of running programs
	- ss -tu : tcp and udp
	- ss -put : + process info
	- ss -4put : + only ipv4
	- ss -4punt : + show ports as numbers
		- Windows equiv is netstat

**Network config**
Three options
- Manual (iproute)
	- immediate but not persistent without network daemon
- static manager (automate initial setup
	- persistent
- dynamic manager (automate and monitor setup)
	- extensible, DHCP

**Manual configs**
- ip lnk set dev  < int > < up } down > : change interface state
- ip address < add / del > < IP / CIDR > dev < int > : add remove interface static ip
- ip route < add / del> < net / CIDR > via < ip > dev < int > : add / remove static ip
- ip route add default via < ip > 
uses name servers listed in /etc/resolv.conf for name lookups
	can be manually updated without network daemon,
	if a daemon is running it will overrite so have to use it

**Static manager**
most use ifupdown or sysconfig to provide persistence
- ifupconfig config : /etc/network/interfaces
- sysconfig : /etc/sysconfig/network
On start-up, init systems will start the static manager
	Daemon then configs the net based on config
- Systemctl restart networking - changes to config require a restart

**Dynamic managers**
Capable of ..
- responding to events
- automatically switching between connections
- integrating VPNs
- performing DHCP
Best and most widely used is NetworkManager, but others include system-networkd, connman and wicd.

**NetworkManager - Dynamic**
Designed to coexist with and respect static managers
	on startup, it will take control of any unmanaged interfaces
	Config interfaces for NM
		nmcli
		nmtui

**Troubleshooting**
DNS
- dig domain.com < record type > : Dns record query
- host -t < record type > domain.com : dns record query
- nslookup domain.com : nameserver ips
- whois < domain | ip > : who owns this
IP
- ping < dest > : host connectivity
- traceroute < dest > : host connectivity path



