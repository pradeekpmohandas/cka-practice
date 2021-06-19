
# basic certificates generated for core components to auth with kube api
  All intercommunication between components require certificates
-------------------------------
kubeApi --> kubeapi.crt kubeapi.key
etcd    --> etcd.crt  etcd.key
kubelet  --> kubelet.crt kubelet.key | each node have kubelet config file 
scheduler --> scheduler.crt scheduler.key
kubeproxy --> kubeproxy.crt kubeproxy.key
-------------------------------
admin user  --> admin.crt admin.key --> to communicate to kubeApi
CA authority --> ca.crt ca.key --> to sign all the above certs --> CERT created 1st (self signed)
-------------------------------

certs should contain group name, for system components prefix "system:"
for admin user prefix "system:master" in group 

# to view cert details 
openssl x509 -in some.crt -text -noout