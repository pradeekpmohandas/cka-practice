new user is nothing but anyone with ca signed certificate which can authenticate to apiserver

user generate csr --> sign using ca cert --> signed crt can authenticate with api server
#csr generate : 1. gen privatekey/pub 2. csr request with  cn name..
controler manger have component to manage csr, signing using ca
kind: CertificateSigningRequest

k certifcate approve <csr-name>

#once approved check the status section to get the issued certificate
the above cert is used to authenticate upon each kubectl common, cert is moved to file called kubeconfig

default location $HOME/.kube/config
kubectl can we used to access multiple cluster with multiple user, this is controlled by kubeconfig file

kubectl config user-context prod-user@production #will check the file content in kubeconfig
