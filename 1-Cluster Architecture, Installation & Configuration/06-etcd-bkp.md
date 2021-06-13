ETCD
export ETCDCTL_API=3

TO BACKUP | to connect to etcd certs are required
Etcdl snapshot save <certs flag> <save director>

TO RESTORE
etcdctl  --data-dir /var/lib/etcd-from-backup snapshot restore /opt/snapshot-pre-boot.db

change mount path in etcd pod to newly restored path 

