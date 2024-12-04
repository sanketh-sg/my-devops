This configures a 1Gi Persistent Volume using the standard storage class. The access mode is set to ReadWriteOnce, which is the only read-write mode supported by this storage class.

The hostPath field determines the volume's configuration by the storage driver. Here, the hostPath provisioner is used. This tells the driver to place the volume's data in the /tmp/static directory on the host machine. Note that if you are using a different storage driver with another provisioner, your configuration options will vary.

Static provision is where we create pv first and create a corresponding pvc and duse it in the pod.

Standard storage class is backed by rancher.io local-path external provisioner

when we create a pv a directory will be created on the host(kind-node) to persist the data.

During dynamic provisioning we create a pvc and attach it to pod and let the storage class handle the creation of pv.

why??
pv and pvc bind when the requested size and access mode match. we cant create pv for every different request.

storage class will take care of creating the pv based on the pvc and what to to with its contents after the pod is destoryed.

On Kind cluster
The rancher.io/local-path provisioner, which you are using, creates local volumes on the node where the pod is scheduled. These volumes are tied to the local filesystem of that specific node.
If a pod is rescheduled to a different node, it will lose access to the data because the storage is not shared across nodes.