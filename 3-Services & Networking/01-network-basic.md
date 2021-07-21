# private ip range | start
10.0.0.0
192.168.0.0
172.16.0.0


# Linux network basic
switch - connect two computers A & B - create network - on network interface which both A/B have
router - connect two or more switch together, has ip on each network / switch it connect to 
cat /proc/sys/net/ipv4/ip_forward #if 1 then packets allowed between network interfaces
cat /proc/sys/net/ipv4/ip_forward #for permanent


# commands
ip link                           #link data link layer info, list interfaces on host
ip addr add 192.168.0.0 dev ethO  #to set ip to interface - ip addr add IP dev INTERFACE_NAME 
route                             #command list routes configured 
ip route                          #command list routes configured 
ip route add 192.168.0.10 via 192.168.1.1        #ip route add IP via GW-IP - to add entry
ip route add default via 192.168.1.1             #internet, wifi router 
ip route add 192.168.0.2 via 0.0.0.0            # no gw, the ip is in the same network


# routing table vs ARP table
Address Resolution Protocol - finding a host's Link Layer (MAC) address when only its IP address is known. The ARP table is used to maintain a correlation between each MAC address and its corresponding IP address.
Routing table - info on how to reach a ip, via which gateway

