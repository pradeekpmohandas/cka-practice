https://stackoverflow.com/questions/58748447/simulating-daemonset-behaviour-with-kind-deployment


# What is the Service CIDR?
kubeapi -service-cluster-ip-range=10.96.0.0/12


# Which Networking (or CNI Plugin) is configured and where is its config file?
/etc/cni/net.d/10-weave.conflist

# location of kubelet config
 /var/lib/kubelet/config

# Write the names of all namespaced Kubernetes resources (like Pod, Secret, ConfigMap...) into /opt/course/16/resources.txt.
k api-resources --namespaced=true


# To test our RBAC setup 
kubectl auth can-i and --as
k -n project-hamster auth can-i create secret  --as system:serviceaccount:project-hamster:processor

# As we cannot kubectl apply or kubectl edit , in this case we need to delete and create or replace:
k -f 9.yaml replace --force

# for nginx
     command:
        - sh
        - -c

# for busybox
    command:
    - /bin/sh
    - -c