# Create a Pod

A Pod is the basic building block of Kubernetes – the smallest and simplest unit in the Kubernetes object model that you create or deploy. A Pod represents a running process on your cluster.

In this example we will create a Pod in our cluster, read its logs, and then delete it.

## Note

> A `Pod` is the first of many resource types that we will interact with in Kubernetes. `kubectl explain` is a great way to quickly take a look at the latest documentation for any given resource.
```bash
kubectl explain pods
```

## Instructions

#### Create Pod:
```bash
kubectl apply -f resources/pod.yaml
```

It's worth noting that Kubernetes will add some additional fields to the pod that we submit to the cluster. To see these changes run:

```bash
kubectl get -f resources/pod.yaml -o yaml | git diff --no-index resources/pod.yaml -
```

The main things to look out for are the additional fields in the `spec` stanza (for default and computed values), and a new `status` stanza which is read-only and used to represent the state of the pod.

To get more information about a field, you can pass the field path to `kubectl explain`:
```bash
kubectl explain pods.spec.containers.imagePullPolicy
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
