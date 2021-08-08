# What is the network interface configured for cluster connectivity on the master node?
ip - command
ip address | ip link | ip route 
ip address | grep "ip of node"

# What is the MAC address of the interface on the master node?
ip a | grep "ip of node"
ip link show eth

# What is the MAC address assigned to node01?
arp #address resolution protocol
arp <node-name>

# What is the port the kube-scheduler is listening on in the controlplane node?
netstat -nplt
listening server sockets -l
program names -p
tcp -t

# Notice that ETCD is listening on two ports. Which of these have more client connections established?
netstat -nplt ==> check whic ports
netstat -anp | grep etcd | grep 2379 | wc -l
2379 is the port of ETCD to which all control plane components connect to. 2380 is only for etcd peer-to-peer connectivity. When you have multiple master nodes. 

ifconfig