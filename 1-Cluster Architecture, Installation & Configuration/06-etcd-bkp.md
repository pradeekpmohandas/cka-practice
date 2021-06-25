# stop kubeapi server before restore
service kube-api
rename yaml static pod

# ETCD use version 3
export ETCDCTL_API=3

# TO BACKUP | to connect to etcd certs are required   (zip file)
Etcdl snapshot save <certs flag> <save director>

# TO RESTORE (unzip file)
etcdctl  --data-dir /var/lib/etcd-from-backup snapshot restore /opt/snapshot-pre-boot.db

# mount the new directory to etcd po
change mount path in etcd pod to newly restored path 

# info
–listen-client-urls 
This flag tells the etcd to accept incoming requests from the clients on the specified scheme://IP:port combinations.