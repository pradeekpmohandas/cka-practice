# 1 Deploy an additional scheduler to the cluster following the given specification #LEARN
make a copy of static scheduler pod in /temp, then edit the following 
- --leader-elect=false
- --port=10282
- --scheduler-name=my-scheduler
- --secure-port=0 #to disabled https
change HTTPS to HTTP n port in health & ready url section

k apply -f deploy-as-a-pod.yaml


# 2 back-up n restore etcd db - do it again #LEARN
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


# redo 
https://kodekloud.com/topic/practice-test-backup-and-restore-methods-2/

https://kodekloud.com/topic/practice-test-certificates-api-2/