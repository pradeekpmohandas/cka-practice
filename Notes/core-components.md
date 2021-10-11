# control plane components - packed with offical k8s project
kube-api server
kube-controller manager
kube-scheduler 
kube-proxy (proxy on each node to create ip table rules, connectivity among all nodes, daemonset), create ip table rules in each node to forward serviceIP -> POD IP 

kubelet - agent on each node
---- 
# other project
etcd cluster
core-dns : dns server for the cluster | not deamon set | save (service-name | service-ip)
kubectl - client to access cluster
netowrk-solution - seperate deploy - calico/fannel/netD/weave. creates a network and responsible to assign the ip to the pod/svc.


# extra notes
Kubelet- cadvisor - collect metrics | in memory metrics collector
kube-controller-manager --pod-eviction-timeout=5m #time it waits to consider node dead/terminate pod

# story line
1) service created is assigned IP by network solution, this svc-name:ip mapping store by dns, kubeproxy helps in proxing to reach in which ever node

2)call to service : request 1st goes to api server -> dns resolve by coreDNS -> gets ip -> using this ip check the ip table rules on node -> forward to that ip:port