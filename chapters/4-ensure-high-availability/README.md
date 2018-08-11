# Ensure High Availability

In this example we will use a [Deployment](https://kubernetes.io/docs/concepts/workloads/controllers/deployment
) resource type to create a redundant and self-healing deployment of our hello-world application.

The goals of this chapter are to:
- Create a service to load balance against three instances of our application
- Evenly distribute instances of our application across available nodes in our cluster
- Use health checks to ensure that instances continue to be able to accept traffic

## Instructions

#### Create Deployment and Service:

```bash
kubectl apply -f resources
```

#### View deployment information:

Verify that the deployment has been rolled out:
```bash
kubectl rollout status deployment myapp-deployment
```

#### Visit the service URL:

```bash
minikube service myapp-svc --url
```

#### Simulate Runtime Error:

Start monitoring running pods:
```bash
kubectl get pod -l app=myapp --watch
```

In a separate terminal window, delete one of the currently running pods:
```bash
kubectl delete pod <pod-name>
```

Observe that a new Pod is created as soon as the targeted Pod is deleted.

#### Remove resources:
```bash
kubectl delete -f resources
```

## References

https://kubernetes.io/docs/concepts/workloads/controllers/deployment

https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-probes

https://kubernetes-v1-4.github.io/docs/user-guide/kubectl/kubectl_rollout
