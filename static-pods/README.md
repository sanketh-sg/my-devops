Static Pods -> These are the pods that are not scheduled by the scheduler.
All our pods that we create are handled by the scheduler to put it on to a node. The components inside the control plane like scheduler, api-server, etcd, control-manager they themself run as pods. 
Scheduler wont look after these pods, kubelet inside the control plane looks after certain folders(etc/kubernetes/manifests) where the manifests for all of them are kept.
If we remove the scheduler no new pods will be created but existing pods run without any issue.

Manaul scheduling can be done by specifying the node name inside yaml and scheduler wont touch it.

Labels & Selectors
Labels are key: value pairs that are associated with pods, deployments, services etc
selector matches these labels to apply config on to the resources.
