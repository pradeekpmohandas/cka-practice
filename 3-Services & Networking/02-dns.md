
/etc/hosts                                   #source of truth of that system
/etc/resolv.conf "nameserver 192.168.0.0"    #to point system to dns server
/etc/nsswitch.conf                     #order of nameresolution default etc/hosts then DNS server, to change
nameserver 8.8.8.8   #public dns server of google
53 #dns default port

# commands apt install dnsutils
ping
nslookup
dig