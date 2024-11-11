1. ![CLUSTER IP working](/loadbalancer/images/clusterip.png)
```bash
kubectl get pods
NAME      READY   STATUS    RESTARTS   AGE
bar-app   1/1     Running   0          8m18s
foo-app   1/1     Running   0          8m46s

kubectl get svc
NAME          TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)   AGE
bar-service   ClusterIP   10.96.51.30     <none>        80/TCP    7m37s
foo-service   ClusterIP   10.96.188.106   <none>        80/TCP    7m30s
kubernetes    ClusterIP   10.96.0.1       <none>        443/TCP   96m

kubectl get svc -o wide
NAME          TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)   AGE     SELECTOR
bar-service   ClusterIP   10.96.51.30     <none>        80/TCP    7m56s   app=bar
foo-service   ClusterIP   10.96.188.106   <none>        80/TCP    7m49s   app=foo
kubernetes    ClusterIP   10.96.0.1       <none>        443/TCP   96m     <none>

curl 10.96.51.30    nix impure
^C Cannot access because Linux VM of Docker is not exposed to host 

docker exec -it kind-control-plane bash
root@kind-control-plane:/# curl 10.96.51.30
bar
root@kind-control-plane:/# ^C
root@kind-control-plane:/# exit
exit
```
2. ![]
