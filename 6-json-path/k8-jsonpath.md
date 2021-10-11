k get nodes -o=jsonpath='{.items[*].metadata.name}' > /opt/outputs/node_names.txt

kubectl config view --kubeconfig=/root/my-kube-config -o jsonpath="{.users[*].name}"


#sorting

k get pv --sort-by=.spec.capacity.storage 

customer column
kubectl get pv  --sort-by=.spec.capacity.storage -o=custom-columns=NAME:.metadata.name,CAPACITY:.spec.capacity.storage


k -n admin2406 get deploy deploy1 -o jsonpath="{.spec.template.spec.containers[0].name}"


k -n admin2406 get deploy --sort-by=.spec.template.spec.containers[0].name  -o=custom-columns=DEPLOYMENT:.spec.template.spec.containers[0].name,CONTAINER_IMAGE:.spec.template.spec.containers[0].image,READY_REPLICAS:.status.availableReplicas,NAMESPACE:.metadata.namespace 

$ kubectl -n admin2406 get deployment -o custom-columns=DEPLOYMENT:.metadata.name,CONTAINER_IMAGE:.spec.template.spec.containers[].image,READY_REPLICAS:.status.readyReplicas,NAMESPACE:.metadata.namespace --sort-by=.metadata.name > /opt/admin2406_data

