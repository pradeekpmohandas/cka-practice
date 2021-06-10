RoleBasedAcessControl

Api server 
-----------
it supports auth via - static password, static tokens, certificates, 3rd part ldap etc
authentication via  serviceAccount (for machines)

-----
Kube api pod env variable [not used]
-- basic-auth-file=user-details.csv #for static 
curl <kube-api> -u user:pass  #for access to kubeAPI
user-details.csv
[user1,pass1,user1_id,groupid]
user-details-token.csv
[user1,token1,user1_id,groupid]
-- basic-auth-file=user-details-token.csv #for static 
curl <kube-api> --header "Authorization : Bearer TOKEN"
----


for certs
-- basic-auth-file=
curl <kube-api> --key admin.key --cert admin.cert --cacert ca.cert  #to call server, these details can be moved to kube-config file 

