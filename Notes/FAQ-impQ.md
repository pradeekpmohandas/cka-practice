#Remove the taint on master/controlplane, which currently has the taint effect of NoSchedule
root@controlplane:~# kubectl taint node controlplane node-role.kubernetes.io/master:NoSchedule-
node/controlplane untainted

#label pod with app=jio
k run jio --image=nginx --labels=app=jio