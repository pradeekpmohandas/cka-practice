# MASTER NODE
to list all available versions         ==> apt-cache madison kubeadm
upgrade kubeadmin                      ==> apt install kubeadm=1.19.0-00
to list cluster versions available     ==> kubeadm upgrade plan
to upgrade cluster                     ==> kubeadm upgrade apply v1.21.x
update -kubelete,kubectl               ==> 
apt-get install -y --allow-change-held-packages kubelet=1.19.0-00 kubectl=1.19.0-00


# WORKER NODE (upgrade kubeadm, kubelet & kubectl)
ssh into node 
upgrade kubeadmin                      ==> apt install kubeadm=1.19.0-00 #same version as master
update -kubelete,kubectl               ==> 
apt-get install -y --allow-change-held-packages kubelet=1.19.0-00 kubectl=1.19.0-00
