# RoleBasedAcessControl

-----------
# Api server 
-----------
it supports auth via - static password, static tokens, certificates, 3rd part ldap etc
authentication via  serviceAccount (for machines)


# static pass & static token

# format
------------------------
user-details.csv
[user1,pass1,user1_id,groupid]
user-details-token.csv
[user1,token1,user1_id,groupid]
------------------------
Kube api pod env variable [not used]
-- basic-auth-file=user-details.csv #for static pass, envVariable of apiserver 
curl <kube-api> -u user:pass  #for access to kubeAPI

-- basic-auth-file=user-details-token.csv #for static token
curl <kube-api> --header "Authorization : Bearer TOKEN"
----


# for certificate based auth
 #envVariable of apiserver for cert based authorization
 - --allow-privileged=true
 - --authorization-mode=Node,RBAC
curl <kube-api> --key admin.key --cert admin.cert --cacert ca.cert 
 #to call server, these details can be 
==> moved the above to a file, we get "kube-config" file  this is used by kubectl to authenticate

