Each node has limited resources as pods gets created they take up the resources.
Scheduler checks for the pod requirement and node availability and spawn the pod.

If the requirement is too large the pod wont be scheduled with insufficient memory error.

If a scheduled pod takes up too much resource when its running and runs out of node resources then the whole pod crashes due to out of memory.
Hence we use Requests and limits which prevents the node crash instead the pod crashes.

Requires metric pod setup before using.
