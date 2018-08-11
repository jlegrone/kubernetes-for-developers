# Manage Deployments

In this example we will update our previous deployment to use a new image version tag, verify that the change is deployed, then roll back the change.

## Instructions

#### Re-create the deployment from part 4:

```bash
kubectl apply -f ../4-ensure-high-availability/resources
```

Verify that the deployment has been rolled out:
```bash
kubectl rollout status deployment myapp-deployment
```

Visit the service URL:
```bash
minikube service myapp-svc --url
```

#### Update deployment:

Note: We must use `apply` here since the deployment resource we are updating already exists.

```bash
kubectl apply -f resources/updated-deployment.yaml && kubectl rollout status deployment myapp-deployment
```

View new version:
```bash
minikube service myapp-svc --url
```

See your deployment history:
```bash
kubectl rollout history deployment myapp-deployment
```

#### Roll back deployment:

```bash
kubectl rollout undo deployment myapp-deployment
```

Observe that the old text-only version of our app is now deployed again.

#### Remove resources:
```bash
kubectl delete -f ../4-ensure-high-availability/resources
```

## References

https://kubernetes-v1-4.github.io/docs/user-guide/kubectl/kubectl_apply/
