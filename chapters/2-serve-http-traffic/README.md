# Serve HTTP Traffic

In this example we will define a Pod capable of serving HTTP traffic and use port-forwarding to see its responses locally.

## Instructions

#### Create Pod:
```bash
kubectl apply -f resources/pod.yaml
```

#### Connect to the Pod locally:
```bash
kubectl port-forward myapp-pod 8001:80
```

Open http://localhost:8001/

#### Review the logs:
```bash
kubectl logs myapp-pod
```

#### Remove resources:
```bash
kubectl delete pod myapp-pod
```

## References

https://kubernetes.io/docs/tasks/access-application-cluster/port-forward-access-application-cluster
