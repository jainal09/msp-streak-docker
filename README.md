# msp-streak-kubernetes
🎉 
## Kube Commands

1. Version
```
kubectl version
```
2. Create Deployment
```
kubectl create deployment deployment-name --image=image:tag
```
3. Expose port as loadbalancer
```
kubectl expose deployment deployment-name --type=LoadBalancer --port=8080
```
4. Get all the running nodes
```
kubectl get nodes
```
5. Get service address
```
kubectl get service
```
6. Watch network services
```
kubectl get service --watch
```
7. See all the kube events
```
kubectl get events --sort-by=.metadata.creationTimestamp
```
8. Update Image in pods
```
kubectl set image deployment [deployment-name] [container name]=[new-image:tag] --record
```
9. Check deployment history
```
kubectl rollout history deployment [deployment-name]
```
10. Check status of rollout
```
kubectl rollout status deployment [deployment-name]
```
11. Undo Deployment
```
kubectl rollout undo deployment [deployment name] --to-revision=2
```
>  revision number can be fetched from `kubectl rollout history deployment [deployment-name]`

12. Pause Deployment 
```
kubectl pause deployment [deployment-name]
```
> unpause for unpausing
13. see logs

```
kubectl logs pod-id
```
For following logs.
```
kubectl logs pod-id -f
```
## Kube Concepts 
1. Pods
Smallest deployable unit is pod.
 Pod contains container. Pod can have multiple containers.
 `kubectl get pods -o wide` to get the detailed info
 of the running pods. 
**Get Details of a Pod:**
- `kubectl get pods`
- Copy pod full name with id
- `kubectl describe pod [pod name with id]`
2. Replica set
Replica set ensures that a given set of pods are running all the time.
`kubectl get replicasets`
to fetch the pod info about replicasets.

**Scale up application by increasing replicaset:**

``` 
kubectl scale deployment deployment-name --replicas=3
```

3. Master Node

Responsible for management of the cluster and its changes. User application doesnt run here. It runs inside worker nodes.
- Api Server

Changes made by the kubectl on our server is an api call to the api server inside kubernetes cluster.
-  Scheduler

Scheduler schedules the pods on a nodes based on resource availability
- Controller Manager

This manages states of cluster.

4. Worker Node
- Node agent (kubelet)

Monitor whatever is happening inside worker node and report it to Master Node.

- Networking Component

It helps you exposing services , ports and loadblancer stuff.

- Container Runtime

Runtime for containers in OCI (open container initerface format).


## Azure CLI
1. Authenticate Kubernetes
```
az aks get-credentials --resource-group [resource-group] --name [kube cluster name]
```
## Miscellenous
1. Watch command to continuously fire api call
```
watch -n 1 curl http://40.71.232.221:8000/polls
```
> -n indicates time interval for api request (in sec)
