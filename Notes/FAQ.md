# Remove the taint on master/controlplane, which currently has the taint effect of NoSchedule
root@controlplane:~# kubectl taint node controlplane node-role.kubernetes.io/master:NoSchedule-
node/controlplane untainted

# label pod with app=jio, can't be done with deploy
k run jio --image=nginx --labels=app=jio,key=value

# Deploy a DaemonSet for FluentD Logging
k create deploy > deploy.yaml
edit - Deamonset, rm replica,  strategy, status

# What is the path of the directory holding the static pod definition files?
1) ps -aux | grep kubelet 
 0:34 /usr/bin/kubelet --bootstrap-kubeconfig=/etc/kubernetes/bootstrap-kubelet.conf --kubeconfig=/etc/kubernetes/kubelet.conf --config=/var/lib/kubelet/config.yaml --network-plugin=cni 
 --pod-infra-container-image=k8s.gcr.io/pause:3.2
2) cat /var/lib/kubelet/config.yaml
shutdownGracePeriodCriticalPods: 0s
staticPodPath: /etc/kubernetes/manifests
or systemctl status kubelet

# Create a static pod named static-busybox that uses the busybox image and the command sleep 1000
kdry run static-busybox --image=busbox --command sleep 1000  

# Deploy an additional scheduler to the cluster following the given specification
make a copy of static scheduler pod in /temp, then edit the following 
- --leader-elect=false
- --port=10282
- --scheduler-name=my-scheduler
- --secure-port=0 #to disabled https
change HTTPS to HTTP n port in health & ready url section

k apply -f deploy-as-a-pod.yaml

# what is the latest upgradable version
kubeadm upgrade plan - list all possible updates of each component

# back-up n restore etcd db - do it again
BACKUP
- need server details to connect to db, endpoint not provided because localhost
ETCDCTL_API=3 etcdctl --cacert="/etc/kubernetes/pki/etcd/ca.crt" --cert="/etc/kubernetes/pki/etcd/server.crt" --key="/etc/kubernetes/pki/etcd/server.key" snapshot save /opt/snapshot-pre-boot.db

- RESTORE -> to new directory which dont exist
ETCDCTL_API=3 etcdctl snapshot restore /opt/snapshot-pre-boot.db --data-dir="/root/etcd-bkp"
- change volume mount
 volumes:
  - hostPath:
      path: /var/lib/etcd-from-backup
      type: DirectoryOrCreate
    name: etcd-data

# if no scheduler directly add a pod to node
---
apiVersion: v1
kind: Pod
metadata:
  name: nginx
spec:
  nodeName: node01
  containers:
  -  image: nginx
     name: nginx


# find static pod location in other node
ps -aux | grep kubelet #check for --config location

# multiple scheduler
- --leader-elect=false
- --port=10282
- --scheduler-name=my-scheduler
- --secure-port=0
https://kubernetes.io/docs/tasks/extend-kubernetes/configure-multiple-schedulers/

# At what address can you reach the ETCD cluster from the controlplane node?
--listen-client-urls

# redo 
https://kodekloud.com/topic/practice-test-backup-and-restore-methods-2/

https://kodekloud.com/topic/practice-test-certificates-api-2/


# imp
kubectl api-resources -o wide
k get nodes --as michelle

# network policy
 - ports:
    - port: 53
      protocol: UDP
    - port: 53
      protocol: TCP
Note: We have also allowed Egress traffic to TCP and UDP port. This has been added to ensure that the internal DNS resolution works from the internal pod. Remember: The kube-dns service is exposed on port 53:


# install using kubeadm
kubeadm init --pod-network-cidr 10.244.0.0/16 --apiserver-advertise-address=192.168.56.2(ip of control plane)


# kubelet location
/var/lib/kubelet/config

# check which port is being used
netstat -tulpn

# Create a new deployment called nginx-deploy, with image nginx:1.16 and 1 replica. Next upgrade the deployment to version 1.17 using rolling update. Make sure that the version upgrade is recorded in the resource annotation.
kubectl set image deployment/nginx-deploy nginx-deploy=nginx:1.17 --record


