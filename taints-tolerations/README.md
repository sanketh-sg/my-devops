Taint -> is a key value pair attached to a node. If any pod needs to be scheduled on the node with a taint it shoukd posses a "Toleration".

Toleration-> is the same key value pair that is on the node. The pods toleration should matchwith taint.

There are three effects,
noSchedule -> applies to newer pods that will be created in future.
noExecute -> applies to existing as well as the new ones.
preferNoSchedule -> There is no guarentee 

kubectl taint node worker-node key=value:EffectType
kubectl taint node worker-node key=value:EffectType- #to remove the taint

control plane node by default has few taints which prevent pods from being scheduled on it.

nodeSelector-> While the taint prevents a pod being created on a node it does not guarentee the pod is created on a specfic node. The pod can still be created on a node without any taint.(If a pod want s to be on a node with taint it should have toleration else it goes to some other node ). Hence we use nodeSelector which scheduled the pod on the 1st matched node.

This drawback of taint along with nodeselectors inability to have multiple conditions gave rise to node affinity.

In node affinity each node has a labels and pods that match the conditions gets scheduled on them.

If there is a label that does not match any node lable it wont be scheduled.(requiredmode) 
If scheduling node has a preference on certain node we can use this mode(preferredmode) But if the preference is not available then the node will be scheduled on any available node.