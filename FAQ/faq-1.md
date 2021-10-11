# 1 Remove the taint on master/controlplane, which currently has the taint effect of NoSchedule
root@controlplane:~# kubectl taint node controlplane node-role.kubernetes.io/master:NoSchedule-
node/controlplane untainted
or edit node

# 2 label pod with app=jio, can't be done with deploy
k run jio --image=nginx --labels=app=jio,key=value

# 3 Deploy a DaemonSet for FluentD Logging
k create deploy > deploy.yaml
edit - Deamonset, rm replica,  strategy, status

# 4 What is the path of the directory holding the static pod definition files?
1) ps -aux | grep kubelet 
 0:34 /usr/bin/kubelet --bootstrap-kubeconfig=/etc/kubernetes/bootstrap-kubelet.conf --kubeconfig=/etc/kubernetes/kubelet.conf --config=/var/lib/kubelet/config.yaml --network-plugin=cni 
 --pod-infra-container-image=k8s.gcr.io/pause:3.2
2) cat /var/lib/kubelet/config.yaml
shutdownGracePeriodCriticalPods: 0s
staticPodPath: /etc/kubernetes/manifests
or systemctl status kubelet

# 5 Create a static pod named static-busybox that uses the busybox image and the command sleep 1000
kdry run static-busybox --image=busbox --command sleep 1000  



# 6 what is the latest upgradable version
kubeadm upgrade plan - list all possible updates of each component


# 7 if no scheduler directly add a pod to node
apiVersion: v1
kind: Pod
metadata:
  name: nginx
spec:
  nodeName: node01
  containers:
  -  image: nginx
     name: nginx


# 8 At what address can you reach the ETCD cluster from the controlplane node?
--listen-client-urls



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


