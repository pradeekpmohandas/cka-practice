k get <kind> -o json 

--sort-by=
-o-custom-columns=

k get po nginx -o jsonpath='{.items[0].spec.containers[0].image}'
$.status.containerStatuses[?(@.name == 'redis-container')].restartCount