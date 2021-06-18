* nodeName: node01 —  when no scheduler present, assign pod go directly to node. This tag will be added to pods automaticaly if it was scheduled by scheduler also.
similar to schedulerName: <>

* nodeSelector: tell scheduler to place in particular node - single key:value, for more advanced expression greater than/less than - nodeaffinity/anti affinity used

* Node affinity is property of pod that attrack them to set of nodes

* anti affinity opposite

* Taints are property of node to repel a set of pods
