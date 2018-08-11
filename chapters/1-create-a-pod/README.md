# Create a Pod

A Pod is the basic building block of Kubernetes – the smallest and simplest unit in the Kubernetes object model that you create or deploy. A Pod represents a running process on your cluster.

In this example we will create a Pod in our cluster, read its logs, and then delete it.

## Instructions

#### Create Pod:
```bash
kubectl apply -f resources/pod.yaml
```

#### Watch the logs:
```bash
kubectl logs myapp-pod --follow
```

#### Remove the Pod:
```bash
kubectl delete pod myapp-pod
```

## References

https://kubernetes.io/docs/concepts/workloads/pods/pod-overview

https://kubernetes-v1-4.github.io/docs/user-guide/kubectl/kubectl_create

https://kubernetes-v1-4.github.io/docs/user-guide/kubectl/kubectl_logs
