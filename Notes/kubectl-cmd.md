to record action  --record
kubectl create deploy.yaml --record #to record deploy 

K run nginx --image=nginx #pod creation
K scale deploy <name> —replicas=2
K create -help
K run httpd --image=httpd:alpine --port=80 --expose
K get all, K get -A
k get pods --no-headers
k get pods --selector env=dev #selection on labels
k get pod --show-labels
k label pods foo key=value

K logs <pod>
K logs <pod> -f -  -previous

k get -o custom-columns and --sort-by
k taint node controlplane role=master:NoSchedule
effect must be NoSchedule(no further scheduling) PreferNoSchedule  NoExecute( evict if any running)
Toleration applied on pod



k run busy —restart=Never --image=busybox  --command sleep  1000

K rollout history deploy/nginx 
k rollout history deploy/nginx --revision=2  #details on specific version
K rollout undo deploy/nginx #one revision undo
 k rollout undo  deploy/nginx --to-revision=2 #to specific version 

K cordon/uncordon nodeName
K drain nodeName

k cluster-info

k get csr
k certificate approve <csr-name-userName>
k certificate deny <csr-name-userName>

#to view the kubeconfig used
k config view 
k - -kubeconfig <kubeconfigfile> get ns

k config set-context <kubernetes-admin@kubernetes-nameofcontext defined in file>
kubectl config --kubeconfig=/root/my-kube-config use-context <research-contextName>


To set context | current-context for working for the current cluster
k config set-context $(k config current-context) --namespace=temp

k proxy #start a proxy server on localhost with credentials supplied by kubeconfig


k auth can-i  <delete deploy> 
k auth can-i  <delete deploy>  —as <dev-user -userName>K run nginx --image=nginx #pod creation
K scale deploy name —replicas=2
K create -help
K run httpd --image=httpd:alpine --port=80 --expose
K get all, K get -A
k get pods --no-headers
k get pods --selector env=dev #selection on labels
k get pod --show-labels
k label pods foo key=value

K logs <pod>
K logs <pod> -f -  -previous

k get -o custom-columns and --sort-by
k taint node controlplane role=master:NoSchedule
effect must be NoSchedule(no further scheduling) PreferNoSchedule  NoExecute( evict if any running)
Toleration applied on pod

k set image po redis <redis container name>=redis

k run busy —restart=Never --image=busybox  --command sleep  1000

k rollout restart deploy
K rollout history deploy/nginx 
k rollout history deploy/nginx --revision=2  #details on specific version
K rollout undo deploy/nginx #one revision undo
k rollout undo  deploy/nginx --to-revision=2 #to specific version 

K cordon/uncordon nodeName
K drain nodeName

k cluster-info

k get csr
k certificate approve <csr-name-userName>
k certificate deny <csr-name-userName>

#to view the kubeconfig used
k config view 
k - -kubeconfig <kubeconfigfile> get ns

k config set-context <kubernetes-admin@kubernetes-nameofcontext defined in file>
kubectl config --kubeconfig=/root/my-kube-config use-context <research-contextName>


To set context | current-context for working for the current cluster
k config set-context $(k config current-context) --namespace=temp

k proxy #start a proxy server on localhost with credentials supplied by kubeconfig


k auth can-i  <delete deploy> 
k auth can-i  <delete deploy>  —as <dev-user -userName>


##########################  CORE  #######################
k rollout
k scale
k run 
k create
k expose 
k describe 
k taint
k label
k config 
k logs
k auth

######################## FLAGS #############
k get po -A 
k get all --no-headers 
k get nodes --show-labels
k get po --selector app=neo
k get po --selector env=prod,bu=finance,tier=frontend
k -n kube-system top pod --sort-by=cpu
k -n kube-system top pod --sort-by=memory


###################### short notes ##############
apps/v1 --> deploy/rs/
v1 --> pod
serviceName.namespace.svc.cluster.local --> fully qualified name
kubernetes svc 6443
--labels only with  #k run po --labels app=neo