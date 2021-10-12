k get <kind> -o json 

--sort-by=
-o-custom-columns=

k get po nginx -o jsonpath='{.items[0].spec.containers[0].image}'
$.status.containerStatuses[?(@.name == 'redis-container')].restartCount


k get nodes -o=jsonpath='{.items[*].metadata.name}' > /opt/outputs/node_names.txt

kubectl config view --kubeconfig=/root/my-kube-config -o jsonpath="{.users[*].name}"


#sorting

k get pv --sort-by=.spec.capacity.storage 

customer column
kubectl get pv  --sort-by=.spec.capacity.storage -o custom-columns=NAME:.metadata.name,CAPACITY:.spec.capacity.storage


k  get deploy deploy1 -o jsonpath="{.spec.template.spec.containers[0].name}"


k  get deploy --sort-by=.spec.template.spec.containers[0].name  -o=custom-columns=DEPLOYMENT:.spec.template.spec.containers[0].name,CONTAINER_IMAGE:.spec.template.spec.containers[0].image,READY_REPLICAS:.status.availableReplicas,NAMESPACE:.metadata.namespace 

$ k get deployment -o custom-columns=DEPLOYMENT:.metadata.name,CONTAINER_IMAGE:.spec.template.spec.containers[].image,READY_REPLICAS:.status.readyReplicas,NAMESPACE:.metadata.namespace --sort-by=.metadata.name > /opt/admin2406_data



k get node -o jsonpath="InternalIP of {.items[*].status.addresses[1].address}"
kubectl get nodes -o jsonpath='{.items[*].status.addresses[?(@.type=="InternalIP")].address}'