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

First, you can inspect the diff that we will be applying:

```bash
git diff --no-index ../4-ensure-high-availability/resources/deployment.yaml resources/updated-deployment.yaml
```

```diff
--- a/../4-ensure-high-availability/resources/deployment.yaml
+++ b/resources/updated-deployment.yaml
@@ -17,7 +17,7 @@ spec:
     spec:
       containers:
       - name: myapp-container
-        image: nginxdemos/hello:plain-text
+        image: nginxdemos/hello:latest
         ports:
         - name: web
           containerPort: 80
```

We can use `kubectl apply` and `kubectl rollout` to apply this change and observe the progression as kubernetes performs a rolling update of our deployment:

```bash
kubectl apply -f resources/updated-deployment.yaml && \
kubectl rollout status deployment myapp-deployment
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
